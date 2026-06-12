---
title: "google docs uploader for unity launcher"
date: 2011-05-28
forum: General Help
---

### Post by TJLeJeune on 2011-05-28
Hey peoples

I've been trying to write a simple google docs uploader for the unity launcher, but i'm unsure of how to get it working correctly. I have very little programing knowlage. I figured the ubuntu forum would be a good place to ask for help since some of you may be interested in it. The launcher should upload files to google docs if a file is dragged and dropped on it and ask the user if they want to open the newly uploaded document.  If the launcher is clicked without a file it should simply open the google docs home site. The launcher should also have a quicklist allowing the user to open a new document, spreadsheet, or presentation. There is a google command line tool in the repos that already handles uploading to google docs called googlecl, so this seems like it would be a fairly simple project.

So far i only have it set up as a .desktop file. Heres what I have so far.

[Desktop Entry]
Version=1.0
Name=Google Docs Upload
Comment=Upload files to google docs
GenericName=Doc Uploader
Exec=google docs upload %u
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=/home/tjl/.googledocs/docs.png
Categories=GTK;Office;
MimeType=application/vnd.oasis.opendocument.text;application/vnd.oasis.opendocument.text-web;application/vnd.oasis.opendocument.text-master;application/vnd.sun.xml.writer;application/vnd.sun.xml.writer.template;application/vnd.sun.xml.writer.global;application/vnd.stardivision.writer;application/msword;application/vnd.ms-word;application/x-doc;application/rtf;text/rtf;application/vnd.wordperfect;application/wordperfect;application/vnd.openxmlformats-officedocument.wordprocessingml.document;application/vnd.ms-word.document.macroenabled.12;application/vnd.openxmlformats-officedocument.wordprocessingml.template;application/vnd.ms-word.template.macroenabled.12;application/vnd.oasis.opendocument.presentation;application/vnd.oasis.opendocument.presentation-template;application/vnd.sun.xml.impress;application/vnd.sun.xml.impress.template;application/vnd.stardivision.impress;application/mspowerpoint;application/vnd.ms-powerpoint;application/vnd.openxmlformats-officedocument.presentationml.presentation;application/vnd.ms-powerpoint.presentation.macroenabled.12;application/vnd.openxmlformats-officedocument.presentationml.template;application/vnd.ms-powerpoint.template.macroenabled.12;application/vnd.oasis.opendocument.spreadsheet;application/vnd.oasis.opendocument.spreadsheet-template;application/vnd.sun.xml.calc;application/vnd.sun.xml.calc.template;application/vnd.stardivision.calc;application/vnd.stardivision.chart;application/msexcel;application/vnd.ms-excel;application/vnd.openxmlformats-officedocument.spreadsheetml.sheet;application/vnd.ms-excel.sheet.macroenabled.12;application/vnd.openxmlformats-officedocument.spreadsheetml.template;application/vnd.ms-excel.template.macroenabled.12;application/vnd.ms-excel.sheet.binary.macroenabled.12;text/csv;application/x-dbf;application/pdf
StartupNotify=true

TargetEnvironment=Unity
Name[en_US]=Google Docs

X-Ayatana-Desktop-Shortcuts=Files;Docs;Spreadsheet;Presentation;
 
[Files Shortcut Group]
Name=Home 
Exec=/usr/bin/chromium-browser --app="https://docs.google.com/#home"
TargetEnvironment=Unity

[Docs Shortcut Group]
Name=Create New Document 
Exec=/usr/bin/chromium-browser --app="https://docs.google.com/document/create?hl=en"
TargetEnvironment=Unity
 
[Spreadsheet Shortcut Group]
Name=Create New Spreadsheet
Exec=/usr/bin/chromium-browser --app="https://spreadsheets.google.com/ccc?new&hl=en"
TargetEnvironment=Unity
 
[Presentation Shortcut Group]
Name=Create New Presentation
Exec=/usr/bin/chromium-browser --app="https://docs.google.com/present/create?hl=en"
TargetEnvironment=Unity


The drag and drop uploading works fine, Im just unsure of how to to get the launcher to open the new document after its been uploaded and how to get the launcher to open the google docs home site if executed without having a file dropped on it.  Any help would be a fantastic.

---

