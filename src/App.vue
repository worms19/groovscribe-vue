<template>
  <body>
    <div id="GrooveWriter">
      <div class="nonPrintable">
        <div id="LeftHandNav">
          <span id="divisionButtonContainer">
            <span id="logoInSubdivision" class="left-button-content"
              ><img src="images/GScribe_Logo_lone_g.svg"
            /></span>
            <span
              class="left-button edit-block"
              id="timeLabel"
              onclick="myGrooveWriter.timeSigPopupOpen();"
              ><span class="left-button-content"
                ><span
                  ><span id="timeSigLabel" class="buttonFraction"
                    ><sup>4</sup>/<sub>4</sub></span
                  ><span id="timeSubLabel">TIME</span></span
                ></span
              ></span
            >
            <span
              class="left-button subdivision edit-block"
              id="subdivision_8ths"
              onclick="myGrooveWriter.changeDivision(8);"
              ><span class="left-button-content"
                ><span
                  ><span class="buttonFraction"><sup>1</sup>/<sub>8</sub></span
                  >NOTES</span
                ></span
              ></span
            >
            <span
              class="left-button subdivision edit-block"
              id="subdivision_16ths"
              onclick="myGrooveWriter.changeDivision(16);"
              ><span class="left-button-content"
                ><span
                  ><span class="buttonFraction"><sup>1</sup>/<sub>16</sub></span
                  >NOTES</span
                ></span
              ></span
            >
            <span
              class="left-button subdivision edit-block"
              id="subdivision_32ths"
              onclick="myGrooveWriter.changeDivision(32);"
              ><span class="left-button-content"
                ><span
                  ><span class="buttonFraction"><sup>1</sup>/<sub>32</sub></span
                  >NOTES</span
                ></span
              ></span
            >
            <span
              class="left-button subdivision edit-block"
              id="subdivision_12ths"
              onclick="myGrooveWriter.changeDivision(12);"
              ><span class="left-button-content"
                ><span
                  ><span class="buttonFraction"><sup>1</sup>/<sub>8</sub></span
                  >TRIPLETS</span
                ></span
              ></span
            >
            <span
              class="left-button subdivision edit-block"
              id="subdivision_24ths"
              onclick="myGrooveWriter.changeDivision(24);"
              ><span class="left-button-content"
                ><span
                  ><span class="buttonFraction"><sup>1</sup>/<sub>16</sub></span
                  >TRIPLETS</span
                ></span
              ></span
            >
            <span
              class="left-button subdivision edit-block"
              id="subdivision_48ths"
              onclick="myGrooveWriter.changeDivision(48);"
              ><span class="left-button-content"
                ><span>MIXED<br />Division</span></span
              ></span
            >

            <span
              class="left-button edit-block"
              id="undoButton"
              onclick="myGrooveWriter.undoCommand();"
              ><span class="left-button-content"
                ><i class="fa fa-undo"></i>&nbsp;&nbsp;Undo</span
              ></span
            >
          </span>
        </div>
        <div id="TopNav" class="fullWidthEle">
          <span id="logoTextUpperLeft"
            ><img src="images/GScribe_Logo_word_stack.svg"
          /></span>
          <span id="upperLeft">
            <span id="metronomeContainer">
              <span id="metronomeLabel">METRONOME:</span>
              <span
                class="metronomeButton"
                id="metronomeOff"
                onclick="myGrooveWriter.setMetronomeFrequency(0);"
                >OFF</span
              >
              <span
                class="metronomeButton"
                id="metronome4ths"
                onclick="myGrooveWriter.setMetronomeFrequency(4);"
                >4th</span
              >
              <span
                class="metronomeButton"
                id="metronome8ths"
                onclick="myGrooveWriter.setMetronomeFrequency(8);"
                >8th</span
              >
              <span
                class="metronomeButton"
                id="metronome16ths"
                onclick="myGrooveWriter.setMetronomeFrequency(16);"
                >16th</span
              >
              <span
                class="metronomeButton Options grooveDB_hidden"
                id="metronomeOptionsAnchor"
                onclick="myGrooveWriter.metronomeOptionsAnchorClick(event);"
                >Options</span
              >
            </span>
          </span>
          <span id="upperRight">
            <span
              class="rightButtons grooveDB_hidden"
              id="permutationAnchor"
              onclick="myGrooveWriter.permutationAnchorClick(event);"
              ><i class="fa fa-bars"></i> Permutations</span
            >
            <span
              class="rightButtons"
              id="groovesAnchor"
              onclick="myGrooveWriter.groovesAnchorClick(event);"
              ><i class="fa fa-bars"></i> Grooves</span
            >
            <span
              class="rightButtons"
              id="helpAnchor"
              onclick="myGrooveWriter.helpAnchorClick(event);"
              ><i class="fa fa-bars"></i> Help</span
            >
          </span>
        </div>
        <div id="midiPlayer" class="fullWidthEle">
          <!-- space for the midiplayer to be attached by the javascript -->
        </div>
      </div>

      <div id="RightHandContent">
        <div class="nonPrintable">
          <div id="PermutationOptions"></div>
        </div>

        <div class="Printable">
          <!-- rendering area -->
          <div id="sheetMusicDiv" class="fullWidthEle">
            <div id="svgTarget" class="svgTarget">
              <!-- space for the SVG sheet music to display -->
            </div>
          </div>
        </div>
        <div class="nonPrintable">
          <p class="warnings">Warnings:</p>
          <div class="warnings" id="diverr"></div>

          <div
            id="sheetMusicTextFields"
            class="fullWidthEle grooveDB_hidden edit-block"
          >
            <span class="sheetMusicTextField"
              ><b>Title:</b>
              <input
                class="sheetMusicInputField"
                id="tuneTitle"
                onchange="myGrooveWriter.refresh_ABC();"
                type="text"
            /></span>
            <span class="sheetMusicTextField"
              ><b>Author:</b>
              <input
                class="sheetMusicInputField"
                id="tuneAuthor"
                onchange="myGrooveWriter.refresh_ABC();"
                type="text"
            /></span>
            <span class="sheetMusicTextField"
              ><b>Comment:</b>
              <input
                class="sheetMusicInputField"
                id="tuneComments"
                onchange="myGrooveWriter.refresh_ABC();"
                type="text"
            /></span>
            <span id="KeyButton"
              ><input
                type="checkbox"
                class="hiddenCheckbox"
                id="showLegend"
                onclick="myGrooveWriter.refresh_ABC();"/><label
                id="LegendLabel"
                for="showLegend"
                ><i class="fa fa-key"></i></label
            ></span>
          </div>

          <div id="musicalInput" class="fullWidthEle edit-block">
            <div id="measureContainer"></div>
          </div>

          <div id="bottomButtonRow" class="fullWidthEle">
            <span
              class="pageBottomButton edit-block"
              id="clearAllNotesButton"
              onclick="event.preventDefault(); myGrooveWriter.clearAllNotes();"
              ><span class="bottomButtonIcon"
                ><i class="fa fa-trash fa-2x"></i></span
              ><span class="bottomButtonLabel">CLEAR ALL</span></span
            >
            <span
              class="pageBottomButton edit-block"
              id="showHideTomsButton"
              onclick="event.preventDefault(); myGrooveWriter.showHideToms(false, false);"
              ><span class="bottomButtonIcon"
                ><i id="icon-tom1" class="fa fa-circle"></i
                ><i id="icon-tom2" class="fa fa-circle-o"></i
                ><i id="icon-tom3" class="fa fa-circle-o"></i></span
              ><span class="bottomButtonLabel">TOMS</span></span
            >
            <span
              class=" grooveDB_hidden pageBottomButton edit-block"
              id="showHideStickingsButton"
              onclick="event.preventDefault(); myGrooveWriter.showHideStickings(false, false);"
              ><span class="bottomButtonLabel">STICKINGS</span></span
            >
            <span
              class=" grooveDB_hidden pageBottomButton"
              id="downloadButton"
              onclick="myGrooveWriter.DownloadAnchorClick();"
              ><span class="bottomButtonIcon"
                ><i class="fa fa-download fa-2x"></i></span
              ><span class="bottomButtonLabel">DOWNLOAD</span></span
            >
            <span
              class=" grooveDB_hidden pageBottomButton"
              id="printButton"
              onclick="myGrooveWriter.printMusic();"
              ><span class="bottomButtonIcon"
                ><i class="fa fa-print fa-2x"></i></span
              ><span class="bottomButtonLabel">PRINT</span></span
            >
            <span
              class=" grooveDB_hidden pageBottomButton"
              id="shareSaveButton"
              onclick="event.preventDefault(); myGrooveWriter.show_FullURLPopup();"
              ><span class="bottomButtonIcon"
                ><i class="fa fa-share fa-2x"></i></span
              ><span class="bottomButtonLabel">SHARE</span></span
            >
          </div>

          <div id="midiTextOutput"></div>

          <span id="hiddenDescription">
            GrooveScribe allows drummers to easily create grooves, listen,
            share, print sheet music, and more. Use the GrooveScribe to create
            new grooves, figure out the groove to your favorite song, or write
            down the groove to your latest tune.
          </span>

          <!-- GrooveDB output area -->
          <div
            id="GrooveDB_MetaData"
            class="grooveDB_show"
            style="display:none;"
          >
            <div id="grooveDBInstructions">
              This is the text that should be added to the GrooveDB for this
              groove. <br />
              <b>Copy and paste it into the GrooveDB edit window </b>
            </div>
            <div>
              <textarea id="GrooveDB_source" class="fullWidthEle"></textarea>
            </div>
          </div>

          <div id="debugDisplayArea">
            <span id="undoStack"></span>
            <span id="redoStack"></span>
            <span id="URLSearchData"></span>
            <!-- ABC notation -->
            <A
              href=""
              id="showHideABC"
              onclick="event.preventDefault(); myGrooveWriter.ShowHideABCResults();"
              >Show/Hide ABC Notation</A
            >

            <div id="ABC_Results">
              ABC Notation is used for rendering the music. You can see what is
              being generated below. You can even edit it. <br />
              NOTE: whenever the page is modified, the ABC Notation below will
              be overwritten automatically. <br />
              For more information about ABC Notation go here:
              <a href="http://abcnotation.com/">http://abcnotation.com/</a>
              <p></p>
              <textarea id="ABCsource" rows="10" cols="72"></textarea>
              <br />
              <button type="button" onclick="myGrooveWriter.displayNewSVG();">
                Re-render the music
              </button>
              <button type="button" onclick="myGrooveWriter.saveABCtoFile();">
                Save ABC to file
              </button>
            </div>
            <span id="debugOutput"></span>
          </div>

          <div id="totalPlayTime"></div>
        </div>
      </div>

      <!-- context menu that will pop up over notes in advaced edit mode or right click -->
      <div class="noteContextMenu">
        <ul id="metronomeOptionsContextMenu" class="list">
          <li
            class="metronomeOptionsContextMenuItem"
            id="metronomeOptionsContextMenuSolo"
            onclick='myGrooveWriter.metronomeOptionsMenuPopupClick("Solo");'
            title="Just hear the metronome."
          >
            Solo
          </li>
          <li
            class="metronomeOptionsContextMenuItem"
            id="metronomeOptionsContextMenuSpeedUp"
            onclick='myGrooveWriter.metronomeOptionsMenuPopupClick("SpeedUp");'
            title="Increase the tempo automatically"
          >
            Auto speed up
          </li>
          <li
            class="metronomeOptionsContextMenuItem"
            id="metronomeOptionsContextMenuCountIn"
            onclick='myGrooveWriter.metronomeOptionsMenuPopupClick("CountIn");'
            title="One measure of metronome count in at the start"
          >
            Count it in
          </li>
          <li
            class="metronomeOptionsContextMenuItem"
            id="metronomeOptionsContextMenuOffTheOne"
            onclick='myGrooveWriter.metronomeOptionsMenuPopupClick("OffTheOne");'
            title="Click on the e, &, or a"
          >
            Offset click
          </li>
          <!--
				<li id="metronomeOptionsContextMenuDropper"   onclick='myGrooveWriter.metronomeOptionsMenuPopupClick("Dropper")'  >Beat Dropper</li>
				-->
        </ul>
      </div>
      <div class="noteContextMenu">
        <ul id="metronomeOptionsOffsetClickContextMenu" class="list">
          <li
            class="metronomeOptionsOffsetClickContextMenuItem menuChecked"
            id="metronomeOptionsOffsetClickContextMenuOnThe1"
            onclick='myGrooveWriter.metronomeOptionsMenuOffsetClickPopupClick("1");'
          >
            Start on "<b>1</b>"
          </li>
          <li
            class="metronomeOptionsOffsetClickContextMenuItem"
            id="metronomeOptionsOffsetClickContextMenuOnTheE"
            onclick='myGrooveWriter.metronomeOptionsMenuOffsetClickPopupClick("E");'
          >
            Start on "<b>E</b>"
          </li>
          <li
            class="metronomeOptionsOffsetClickContextMenuItem"
            id="metronomeOptionsOffsetClickContextMenuOnTheAND"
            onclick='myGrooveWriter.metronomeOptionsMenuOffsetClickPopupClick("AND");'
          >
            Start on "<b>&amp;</b>"
          </li>
          <li
            class="metronomeOptionsOffsetClickContextMenuItem"
            id="metronomeOptionsOffsetClickContextMenuOnTheA"
            onclick='myGrooveWriter.metronomeOptionsMenuOffsetClickPopupClick("A");'
          >
            Start on "<b>A</b>"
          </li>
          <li
            class="metronomeOptionsOffsetClickContextMenuItem"
            id="metronomeOptionsOffsetClickContextMenuOnTheROTATE"
            onclick='myGrooveWriter.metronomeOptionsMenuOffsetClickPopupClick("ROTATE");'
          >
            Rotate through
          </li>
        </ul>
      </div>
      <div class="noteContextMenu">
        <ul id="metronomeOptionsOffsetClickForTripletsContextMenu" class="list">
          <li
            class="metronomeOptionsOffsetClickContextMenuItem menuChecked"
            id="metronomeOptionsOffsetClickContextMenuOnThe1Triplet"
            onclick='myGrooveWriter.metronomeOptionsMenuOffsetClickPopupClick("1");'
          >
            Start on "<b>1</b>"
          </li>
          <li
            class="metronomeOptionsOffsetClickContextMenuItem"
            id="metronomeOptionsOffsetClickContextMenuOnTheTI"
            onclick='myGrooveWriter.metronomeOptionsMenuOffsetClickPopupClick("TI");'
          >
            Start on "<b>&amp;</b>"
          </li>
          <li
            class="metronomeOptionsOffsetClickContextMenuItem"
            id="metronomeOptionsOffsetClickContextMenuOnTheTA"
            onclick='myGrooveWriter.metronomeOptionsMenuOffsetClickPopupClick("TA");'
          >
            Start on "<b>A</b>"
          </li>
          <li
            class="metronomeOptionsOffsetClickContextMenuItem"
            id="metronomeOptionsOffsetClickContextMenuOnTheROTATE"
            onclick='myGrooveWriter.metronomeOptionsMenuOffsetClickPopupClick("ROTATE");'
          >
            Rotate through
          </li>
        </ul>
      </div>
      <div class="noteContextMenu">
        <ul id="stickingContextMenu" class="list">
          <li onclick='myGrooveWriter.notePopupClick("sticking", "off");'>
            Off
          </li>
          <li onclick='myGrooveWriter.notePopupClick("sticking","right");'>
            <b>R</b>ight
          </li>
          <li onclick='myGrooveWriter.notePopupClick("sticking","left");'>
            <b>L</b>eft
          </li>
          <li onclick='myGrooveWriter.notePopupClick("sticking","both");'>
            <b>R/L</b>
          </li>
          <li onclick='myGrooveWriter.notePopupClick("sticking", "count");'>
            Count
          </li>
        </ul>
      </div>
      <div class="noteContextMenu">
        <ul id="hhContextMenu" class="list">
          <li onclick='myGrooveWriter.notePopupClick("hh", "off");'>Off</li>
          <li onclick='myGrooveWriter.notePopupClick("hh","normal");'>
            Hi-hat normal
          </li>
          <li onclick='myGrooveWriter.notePopupClick("hh","open");'>
            Hi-hat open
          </li>
          <!-- <li onclick='myGrooveWriter.notePopupClick("hh","close");'>Hi-hat closed</li> -->
          <li onclick='myGrooveWriter.notePopupClick("hh","accent");'>
            Hi-hat accent
          </li>
          <li onclick='myGrooveWriter.notePopupClick("hh","crash");'>Crash</li>
          <li onclick='myGrooveWriter.notePopupClick("hh","ride");'>Ride</li>
          <li onclick='myGrooveWriter.notePopupClick("hh","ride_bell");'>
            Ride Bell
          </li>
          <li onclick='myGrooveWriter.notePopupClick("hh","cow_bell");'>
            Cow Bell
          </li>
          <li onclick='myGrooveWriter.notePopupClick("hh","stacker");'>
            Stacker
          </li>
          <li onclick='myGrooveWriter.notePopupClick("hh","metronome_normal");'>
            Click
          </li>
          <li onclick='myGrooveWriter.notePopupClick("hh","metronome_accent");'>
            Click - accent
          </li>
        </ul>
      </div>
      <div class="noteContextMenu">
        <ul id="tom1ContextMenu" class="list">
          <li onclick='myGrooveWriter.notePopupClick("tom1", "off");'>Off</li>
          <li onclick='myGrooveWriter.notePopupClick("tom1", "normal");'>
            Tom Normal
          </li>
        </ul>
      </div>
      <div class="noteContextMenu">
        <ul id="tom4ContextMenu" class="list">
          <li onclick='myGrooveWriter.notePopupClick("tom4", "off");'>Off</li>
          <li onclick='myGrooveWriter.notePopupClick("tom4", "normal");'>
            Tom Normal
          </li>
        </ul>
      </div>
      <div class="noteContextMenu">
        <ul id="snareContextMenu" class="list">
          <li onclick='myGrooveWriter.notePopupClick("snare", "off");'>Off</li>
          <li onclick='myGrooveWriter.notePopupClick("snare", "normal");'>
            Snare Normal
          </li>
          <li onclick='myGrooveWriter.notePopupClick("snare", "accent");'>
            Snare Accent
          </li>
          <li onclick='myGrooveWriter.notePopupClick("snare", "ghost");'>
            Ghost Note
          </li>
          <li onclick='myGrooveWriter.notePopupClick("snare", "xstick");'>
            Cross Stick
          </li>
          <li onclick='myGrooveWriter.notePopupClick("snare", "buzz");'>
            Buzz Stroke
          </li>
          <li onclick='myGrooveWriter.notePopupClick("snare", "flam");'>
            Flam
          </li>
        </ul>
      </div>
      <div class="noteContextMenu">
        <ul id="kickContextMenu" class="list">
          <li onclick='myGrooveWriter.notePopupClick("kick", "off");'>Off</li>
          <li onclick='myGrooveWriter.notePopupClick("kick", "normal");'>
            Kick Normal
          </li>
          <li onclick='myGrooveWriter.notePopupClick("kick", "splash");'>
            Hi-hat foot
          </li>
          <li
            onclick='myGrooveWriter.notePopupClick("kick", "kick_and_splash");'
          >
            Kick &amp; Hi-hat foot
          </li>
        </ul>
      </div>
      <div class="noteContextMenu">
        <ul id="stickingsLabelContextMenu" class="list">
          <li
            onclick='myGrooveWriter.noteLabelPopupClick("stickings", "all_off");'
          >
            all <b>Off</b>
          </li>
          <li
            onclick='myGrooveWriter.noteLabelPopupClick("stickings", "alternate");'
          >
            alternate <b>R</b>/<b>L</b>
          </li>
          <li
            onclick='myGrooveWriter.noteLabelPopupClick("stickings", "all_right");'
          >
            all <b>R</b>s
          </li>
          <li
            onclick='myGrooveWriter.noteLabelPopupClick("stickings", "all_left");'
          >
            all <b>L</b>s
          </li>
          <li
            onclick='myGrooveWriter.noteLabelPopupClick("stickings", "all_count");'
          >
            <b>C</b>ounts
          </li>
          <li
            onclick='myGrooveWriter.noteLabelPopupClick("stickings", "cancel");'
          >
            cancel
          </li>
        </ul>
      </div>
      <div class="noteContextMenu">
        <ul id="hhLabelContextMenu" class="list">
          <li onclick='myGrooveWriter.noteLabelPopupClick("hh", "all_off");'>
            all Hi-hats <b>Off</b>
          </li>
          <li onclick='myGrooveWriter.noteLabelPopupClick("hh", "all_on");'>
            all Hi-hats <b>On</b>
          </li>
          <li onclick='myGrooveWriter.noteLabelPopupClick("hh", "downbeats");'>
            downbeats
          </li>
          <li onclick='myGrooveWriter.noteLabelPopupClick("hh", "upbeats");'>
            upbeats
          </li>
          <li
            id="mute_hh_menu_item"
            onclick='myGrooveWriter.noteLabelPopupClick("hh", "mute");'
          >
            mute HH sound
          </li>
          <li onclick='myGrooveWriter.noteLabelPopupClick("hh", "cancel");'>
            cancel
          </li>
        </ul>
      </div>
      <div class="noteContextMenu">
        <ul id="tom1LabelContextMenu" class="list">
          <li onclick='myGrooveWriter.noteLabelPopupClick("tom1", "all_off");'>
            all Toms <b>Off</b>
          </li>
          <li onclick='myGrooveWriter.noteLabelPopupClick("tom1", "all_on");'>
            all Toms <b>On</b>
          </li>
          <li
            id="mute_tom1_menu_item"
            onclick='myGrooveWriter.noteLabelPopupClick("tom1", "mute");'
          >
            mute tom sound
          </li>
          <li onclick='myGrooveWriter.noteLabelPopupClick("tom1", "cancel");'>
            cancel
          </li>
        </ul>
      </div>
      <div class="noteContextMenu">
        <ul id="tom4LabelContextMenu" class="list">
          <li onclick='myGrooveWriter.noteLabelPopupClick("tom4", "all_off");'>
            all Toms <b>Off</b>
          </li>
          <li onclick='myGrooveWriter.noteLabelPopupClick("tom4", "all_on");'>
            all Toms <b>On</b>
          </li>
          <li
            id="mute_tom4_menu_item"
            onclick='myGrooveWriter.noteLabelPopupClick("tom4", "mute");'
          >
            mute tom sound
          </li>
          <li onclick='myGrooveWriter.noteLabelPopupClick("tom4", "cancel");'>
            cancel
          </li>
        </ul>
      </div>
      <div class="noteContextMenu">
        <ul id="snareLabelContextMenu" class="list">
          <li onclick='myGrooveWriter.noteLabelPopupClick("snare", "all_off");'>
            all Snares <b>Off</b>
          </li>
          <li onclick='myGrooveWriter.noteLabelPopupClick("snare", "all_on");'>
            all <b>Accented</b>
          </li>
          <li
            onclick='myGrooveWriter.noteLabelPopupClick("snare", "all_on_normal");'
          >
            all <b>Normal</b>
          </li>
          <li
            onclick='myGrooveWriter.noteLabelPopupClick("snare", "all_on_ghost");'
          >
            all <b>Ghosts</b>
          </li>
          <li
            id="mute_snare_menu_item"
            onclick='myGrooveWriter.noteLabelPopupClick("snare", "mute");'
          >
            mute snare sound
          </li>
          <li onclick='myGrooveWriter.noteLabelPopupClick("snare", "cancel");'>
            cancel
          </li>
        </ul>
      </div>
      <div class="noteContextMenu">
        <ul id="kickLabelContextMenu" class="list">
          <li onclick='myGrooveWriter.noteLabelPopupClick("kick", "all_off");'>
            all Kicks <b>Off</b>
          </li>
          <li onclick='myGrooveWriter.noteLabelPopupClick("kick", "all_on");'>
            all Kicks <b>On</b>
          </li>
          <li
            onclick='myGrooveWriter.noteLabelPopupClick("kick", "hh_foot_nums_on");'
          >
            HH foot #'s <b>On</b>
          </li>
          <li
            onclick='myGrooveWriter.noteLabelPopupClick("kick", "hh_foot_ands_on");'
          >
            HH foot &'s <b>On</b>
          </li>
          <li
            id="mute_kick_menu_item"
            onclick='myGrooveWriter.noteLabelPopupClick("kick", "mute");'
          >
            mute kick sound
          </li>
          <li onclick='myGrooveWriter.noteLabelPopupClick("kick", "cancel");'>
            cancel
          </li>
        </ul>
      </div>
      <div class="noteContextMenu">
        <ul id="permutationContextMenu" class="list">
          <li onclick='myGrooveWriter.permutationPopupClick("none");'>
            <b>None</b>
          </li>
          <li onclick='myGrooveWriter.permutationPopupClick("kick_16ths");'>
            <b>Kick</b> Permutation
          </li>
          <li onclick='myGrooveWriter.permutationPopupClick("snare_16ths");'>
            <b>Snare</b> Permutation
          </li>
        </ul>
      </div>
      <div class="noteContextMenu">
        <ul id="helpContextMenu" class="list">
          <li onclick='myGrooveWriter.helpMenuPopupClick("undo");'>
            Undo (Ctrl-Z)
          </li>
          <li onclick='myGrooveWriter.helpMenuPopupClick("redo");'>
            Redo (Ctrl-Y)
          </li>
          <li onclick='myGrooveWriter.helpMenuPopupClick("help");'>Help</li>
          <li onclick='myGrooveWriter.helpMenuPopupClick("about");'>About</li>
        </ul>
      </div>
      <div class="noteContextMenu">
        <ul id="downloadContextMenu" class="list" style="width: 200px;">
          <li onclick="myGrooveWriter.SVG_save_as();">
            <b>Download SVG Images</b>
          </li>
          <li onclick="myGrooveWriter.PNG_save_as();">
            <b>Download PNG Images</b>
          </li>
          <li onclick="myGrooveWriter.MIDI_save_as();">
            <b>Download MIDI file</b>
          </li>
        </ul>
      </div>
      <div id="grooveListWrapper"></div>

      <!-- dialog for the TIME label, hidden by default -->
      <div id="timeSigPopup">
        <div id="timeSigPopupTitle">Choose a Time Signature</div>
        <div id="timeSigPopupOptions">
          <select id="timeSigPopupTimeSigTop">
            <option value="2">2</option>
            <option value="3">3</option>
            <option selected value="4">4</option>
            <option value="5">5</option>
            <option value="6">6</option>
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
            <option value="11">11</option>
            <option value="12">12</option>
            <option value="13">13</option>
            <option value="14">14</option>
            <option value="15">15</option>
          </select>
          <b id="timeSigPopupSlash">/</b>
          <select id="timeSigPopupTimeSigBottom">
            <option selected value="4">4</option>
            <option value="8">8</option>
            <option value="16">16</option>
          </select>
        </div>
        <div id="timeSigPopupButtons">
          <button
            id="timeSigPopupCancel"
            onclick="myGrooveWriter.timeSigPopupClose('cancel');"
          >
            Cancel
          </button>
          <button
            id="timeSigPopupOK"
            onclick="myGrooveWriter.timeSigPopupClose('ok');"
          >
            Done
          </button>
        </div>
      </div>

      <!-- this is used by the share/save button, and is hidden by default -->
      <div id="fullURLPopup">
        <span
          id="fullURLPopupCloseButton"
          onclick="myGrooveWriter.close_FullURLPopup();"
          ><i class="fa fa-lg fa-times-circle"></i
        ></span>
        <div id="fullURLPopupTitle">Share Your Groove</div>
        <div id="fullURLPopupSubTitle">
          Use this URL to share or save this groove
        </div>
        <div id="fullURLPopupSubSubTitle">
          (You can also bookmark this page)
        </div>
        <div id="fullURLPopupCheckboxes">
          <span
            ><label id="shortURLLabel" class="fullURLPopupCheckboxLabel"
              ><input
                type="checkbox"
                id="shortenerCheckbox"
                onchange="myGrooveWriter.shortenerCheckboxChanged();"
              />Short URL</label
            ></span
          >
          <span
            ><label id="embedCodeLabel" class="fullURLPopupCheckboxLabel"
              ><input
                type="checkbox"
                id="embedCodeCheckbox"
                onchange="myGrooveWriter.embedCodeCheckboxChanged();"
              />Embed Code</label
            ></span
          >
        </div>
        <div id="fullURLPopupTextFieldContainer">
          <input type="text" id="fullURLPopupTextField" />
        </div>
        <br />
        <div id="shareButtonContainer">
          <button
            id="fullURLPopupCopyButton"
            onclick="myGrooveWriter.copyShareURLToClipboard();"
          >
            &nbsp;<i class="fa fa-copy"></i> &nbsp;COPY&nbsp;
          </button>
          &nbsp; &nbsp; &nbsp;
          <share-button id="shareButton"></share-button>
        </div>
      </div>

      <!-- this is used by the metronome auto speed up option menu, and is hidden by default -->
      <div id="metronomeAutoSpeedupConfiguration">
        <div id="metronomeAutoSpeedupOutputText">
          Increase
          <span id="metronomeAutoSpeedupTempoIncreaseAmountOutput">5</span> bpm
          in
          <span id="metronomeAutoSpeedupTempoIncreaseIntervalOutput">2</span>
          min
        </div>
        <div id="metronomeAutoSpeedupConfigurationKeepIncreasing">
          <input
            type="checkbox"
            checked
            id="metronomeAutoSpeedUpKeepGoingForever"
          /><label for="metronomeAutoSpeedUpKeepGoingForever"
            >Keep increasing after the first interval</label
          >
        </div>
        <div id="metronomeAutoSpeedupConfigurationSliders">
          <div id="metronomeAutoSpeedupConfigurationAmountLable">
            Amount in BPM
          </div>
          <input
            type="range"
            min="1"
            max="100"
            value="5"
            class="metronomeAutoSpeedUpRange"
            id="metronomeAutoSpeedupTempoIncreaseAmount"
            oninput="myGrooveWriter.updateRangeLabel(event, 'metronomeAutoSpeedupTempoIncreaseAmountOutput');"
          />
          <div id="metronomeAutoSpeedupConfigurationIntervalLable">
            Interval in Minutes
          </div>
          <input
            type="range"
            min="1"
            max="20"
            value="2"
            class="metronomeAutoSpeedUpRange"
            id="metronomeAutoSpeedupTempoIncreaseInterval"
            step="1"
            oninput="myGrooveWriter.updateRangeLabel(event, 'metronomeAutoSpeedupTempoIncreaseIntervalOutput');"
          />
        </div>
        <div id="metronomeAutoSpeedupCloseButtonDiv">
          <button
            id="metronomeAutoSpeedupConfigurationCloseButton"
            onclick="myGrooveWriter.close_MetronomeAutoSpeedupConfiguration('ok');"
          >
            Done
          </button>
        </div>
      </div>
    </div>
  </body>
</template>

<script>
export default {
  name: "App",
};
</script>

<style>
/* Part of the Groove Scribe Application
 *
 * This file is only included when debug mode is on.
 * ?Debug=1 in the URL enables Debug mode
 */
#permutationAnchor {
  display: inline-block; /* enabled for debug mode */
}
#showHideABC {
  display: inline-block;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

/* this is for debugging layout issues - puts a read border around everything */
/* body * { border: 1px solid red; }		 */
body {
}
.warnings {
  font-family: monospace;
  display: none;
}
.Printable {
  display: block;
}
.nonPrintable {
  display: block;
}

/* there is another .svgTarget definitiion in groove_writer.css */
.svgTarget {
  width: 100%;
}
.svgTarget svg {
  width: 100%;
  height: calc(
    100%
  ); /* hack, should really be auto, but that causes old webkit to go nuts */
}
.playerControl {
  display: inline-block;
  background-color: #eeeeee;
  width: 100%; /* expand to the surounding element */
  font-family: "Lato", sans-serif;
  white-space: nowrap;
}
.playerControl.large {
  display: block;
  width: 100%;
  min-width: 450px;
  border: 1px solid #ddd;
  padding-left: 0px;
  margin: 0px 0px 0px 0px;
  -webkit-border-radius: 5px;
  -moz-border-radius: 5px;
  border-radius: 5px;
}
.playerControl.small {
  width: 90px;
  border: 1px solid #009;
  padding-left: 0px;
}
.playerControlsRow {
  /border: 1px solid red;
  display: flex;
  display: -webkit-flex;
  padding-left: 6px;
  flex-flow: flex-start;
  flex-wrap: nowrap;
  -webkit-flex-flow: flex-start;
  -webkit-flex-wrap: nowrap;
}
.playerControlsRow.large,
.playerControlsRow.small {
  padding-left: 0px;
}
.midiPlayImage,
.midiRepeatImage,
.midiGSLogo {
  width: 40px;
  height: 40px;
  cursor: pointer;
  flex: none;
  -webkit-flex: none;
  margin: 4px 0px 4px 0px;
  border: 0px solid #000;
  color: #eee;
  font-size: 20px;
  font-family: FontAwesome;
  text-align: center;
  line-height: 40px;
  vertical-align: middle;
  border-radius: 50%;
}
.midiPlayImage,
.midiRepeatImage {
  background: #999;
  margin: 4px 4px 4px 4px;
}
.midiPlayImage:hover,
.midiRepeatImage:hover {
  color: #68c2ff;
  background: #005483;
}
.midiExpandImage {
  font-family: FontAwesome;
  font-size: 26px;
  line-height: 40px;
  transition: all 0.6s ease-in-out;
  width: 40px;
  height: 40px;
  cursor: pointer;
  flex: none;
  -webkit-flex: none;
  margin: 4px 0px 4px 0px;
  color: #999;
  text-align: center;
  vertical-align: middle;
  border-radius: 50%;
}
.midiExpandImage.small:hover {
  color: #666;
  transform: scale(1.4);
}
.midiExpandImage.large:hover {
  color: #666;
  transform: scale(0.8);
}
.midiPlayImage.Stopped:before,
.midiPlayImage.Paused:before {
  letter-spacing: -3px;
  content: "\f04b";
}
.midiPlayImage.Playing:before {
  content: "\f04c";
}
.midiExpandImage.small:before {
  letter-spacing: -3px;
  content: "\f065";
}
.midiExpandImage.large:before {
  letter-spacing: -3px;
  content: "\f066";
}
.midiGSLogo {
  padding-top: 6px;
  width: 20px;
  height: 30px;
}
.midiMetronomeImage {
  margin-top: 9px;
  width: 30px;
  height: 30px;
}
.midiMetronomeImage path {
  fill: #df8600;
}
.midiMetronomeImage:hover path {
  fill: #df8600;
}
.midiMetronomeMenu.selected .midiMetronomeImage path {
  fill: #999;
}
.tempoAndProgress {
  padding-top: 2px;
  width: 100%;
  height: 46px;
  flex: 1;
  -webkit-flex: 1;
}
.tempoAndProgress.small,
.midiGSLogo.small,
.midiMetronomeMenu.small {
  display: none;
}
.tempoRow,
.swingRow {
  /border: 1px solid red;
  display: flex;
  display: -webkit-flex;
  height: 22px;
  flex-flow: flex-start;
  flex-wrap: nowrap;
  -webkit-flex-flow: flex-start;
  -webkit-flex-wrap: nowrap;
}
.tempoInput,
.swingInput {
  background-color: 3f91e5;
  padding: 0px;
  margin-top: 4px;
  margin-right: 2%;
  color: #66c0fe;
  width: 90%;
  flex: 1;
  -webkit-flex: 1;
}
.tempoSettings {
  color: #fff;
}
.tempoLabel,
.swingLabel {
  text-align: right;
  padding-top: 0px;
  font-size: 16px;
  width: 60px;
  color: #999;
}
.tempoOutput,
.swingOutput {
  display: inline-block;
  text-align: left;
  padding-top: 0px;
  font-size: 16px;
  color: #666;
  padding-left: 8px;
  width: 34px;
  flex: none;
  -webkit-flex: none;
}
.swingSettings {
  color: #fff;
}
.MIDIProgressRow {
  display: none;
}
.MIDIProgressRow.large {
  display: block;
  margin-left: 60px;
  display: flex;
  display: -webkit-flex;
  flex-flow: flex-start;
  flex-wrap: nowrap;
  -webkit-flex-flow: flex-start;
  -webkit-flex-wrap: nowrap;
  white-space: nowrap;
  height: 20px;
}
.MIDIProgressRow.small {
  display: block;
  margin-left: 8px;
  padding: 0px;
}
.MIDIPlayTime {
  display: inline-block;
  width: 100px;
  color: #999;
  font-size: 30px;
  margin-left: 6px;
  padding-top: 4px;
  text-align: left;
  line-height: 40px;
  flex: none;
  -webkit-flex: none;
}
.MIDIPlayTime.small {
  display: none;
}
.MIDIProgress {
  width: 85%;
  height: 8px;
  font-size: 0px;
}
.MIDIProgress.small {
  width: 80px;
}
.MIDIProgress.large {
  margin-top: 3px;
}

#ABCSource {
  font-family: monospace;
  font-size: 14px;
}

button {
  cursor: pointer;
}

.abcr {
  /* rectangles enclosing notes in ABC SVG */
  fill: transparent;
  fill-opactity: 0.25;
}
.abcr.highlighted {
  fill: #990000 !important;
  fill-opacity: 0.25;
}

input[type="range"] {
  -webkit-appearance: none;
  width: 100%;
  background-color: #eee;
}
input[type="range"]:before {
  /* set this color for the runnable-track left of the thumb color */
  color: #999;
}
input[type="range"]:after {
  /* set this color for the runnable-track right of the thumb color */
  color: #666;
}
input[type="range"]:focus {
  outline: none;
}
input[type="range"]::-webkit-slider-runnable-track {
  width: 100%;
  height: 8.4px;
  cursor: pointer;
  background: #999;
  border-radius: 6px;
  border: 0px solid #010101;
}
input[type="range"]::-webkit-slider-thumb {
  border: 1px solid #666;
  height: 18px;
  width: 18px;
  border-radius: 20px;
  background: #fff;
  cursor: pointer;
  -webkit-appearance: none;
  margin-top: -6px;
}
input[type="range"]:focus::-webkit-slider-runnable-track {
  background: #0067a3;
}
input[type="range"]::-moz-range-track {
  width: 100%;
  height: 8.4px;
  cursor: pointer;
  background: #666;
  border-radius: 6px;
  border: 0px solid #010101;
}
input[type="range"]::-moz-range-thumb {
  border: 1px solid #666;
  height: 18px;
  width: 18px;
  border-radius: 20px;
  background: #fff;
  cursor: pointer;
}
input[type="range"]::-ms-track {
  width: 100%;
  height: 8.4px;
  cursor: pointer;
  background: transparent;
  border-color: transparent;
  color: transparent;
}
input[type="range"]::-ms-fill-lower {
  background: #49b4f8;
  border: 0px solid #010101;
  border-radius: 2.6px;
}
input[type="range"]::-ms-fill-upper {
  background: #005789;
  border: 0px solid #010101;
  border-radius: 6px;
}
input[type="range"]::-ms-thumb {
  border: 1px solid #666;
  height: 18px;
  width: 18px;
  border-radius: 20px;
  background: #fff;
  cursor: pointer;
}
input[type="range"]:active::-moz-range-thumb {
  background: #fff;
}
input[type="range"]:active::-webkit-slider-thumb {
  background: #fff;
}
@media print {
  /* keep at bottom so it overrides the styles above */
  body {
    margin: 0;
    padding: 0;
    border: 0;
    background-color: transparent;
  }
  div.newpage {
    page-break-before: always;
  }
  div.nobrk {
    page-break-inside: avoid;
  }

  .nonPrintable {
    display: none !important;
  }
}
</style>
