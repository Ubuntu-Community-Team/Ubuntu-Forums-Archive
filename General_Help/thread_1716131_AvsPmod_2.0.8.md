---
title: "AvsPmod 2.0.8"
date: 2011-03-28
forum: General Help
---

### Post by yoyoangel on 2011-03-28
AvsP was an awesome script editor for AviSynth, so it was sad to see that the project was apparently dead.

We have been continuing this project under the name AvsPmod, and there are now many new features and bug fixes, primarily thanks to the work of Angel_Su.

Changelog
Version 2.0.8:
- Customize the autocomplete list (options>Text1)
- support c-style comment '/*...*/', nesting comment '[*...[*...*]...*]' and keyword comment '__END__'
- No delay when zooming
- a new control '\T\T' helps prevent truncation of status bar information
- frame count text turns red if the current position is a bookmark
- draw a blue triangle for a titled bookmark
- fix delay when using many bookmarks
- change the behaivor of clicking on a calltip to close it. Clicking with ALT/CTRL/SHIFT to open the URL 
- keep user's frame/time input in right-click context menu when focus is lost
- Added "Flip" menu to flip the output display
- Added "SwapUV" to the RGB->YUV menu
- new "Save bookmarks to bmp" macro
- Added/Updated some plugin function definitions

Version 2.0.7:
- Function definitions can be imported from avs/avsi files.
- Many new bookmarking features including titles and matroska importer
- Error messages can be grabbed using OCR via a macro
- more formats for saving images
- YUV->RGB menu for selecting different color matrix for preview
- Removed menu item for associating with avs files, because it doesn't work on most operating systems
- several small changes and bugfixes

Version 2.0.6:
- Updated the code base to be compatible with Python 2.7 and wxPython 2.8
- rework the code causing customized filter definitions lost
- add a new 'using Dissolve' option for trim dialog.
- shortcuts dialog is resizable, no longer displays an error
- fix 'tab' character having the wrong width when using monospaced font
- build process has been simplified
- many other minor bugfixes and changes
- Several user function definitions contributed by RiCON

Version 2.0.5:
- Updated defaults for 14 core filters, and added a handful of definitions for some userscripts
- Restored the mp4 encoding tool, as I had mistakenly decided that it was broken. In fact, only the presets were outdated. I have included new x264 presets, and also added the ability to set a CRF rather than a bitrate.
- Added new macro which lets you create a chapter list from your bookmarks. AvsPmod is now a great tool for creating matroska chapter files.
- Added new menu items: 'Open Avisynth plugins folder' & 'Open macros folder'

Version 2.0.4:
- Fixed arrow keys not working in the text area
- Fixed icon not appearing in vista/7
- Fixed custom function definitions not being saved (bug existed in avsp 2.0.2) [this fix may introduce a new bug]
- Included MSVCP71.dll, which may be needed on some systems
- Added some additional default file extension templates
- Added some macros

Version 2.0.3:
- Fixed clipboard data being deleted when closing AvsP
- Included avs2avi.exe
- Removed outdated encoding gui from the tools menu

Known Issues
- Video preview does not work with 64-bit avisynth.

New product explanations
[http://www.brandsdragon.com/products/product_34059.htm](http://www.brandsdragon.com/products/product_34059.htm)

---

