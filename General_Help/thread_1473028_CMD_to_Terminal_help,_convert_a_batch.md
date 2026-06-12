---
title: "CMD to Terminal help, convert a batch"
date: 2010-05-04
forum: General Help
---

### Post by ironic.demise on 2010-05-04
10.4 Ubuntu. Using Apache AND/OR opera unite web server

Wondered if there was an alternative to these commans
Set /p=
Echo
@acho off
type
Redirects (> >> < << |)
rem
IF EXIST GOTO
del
Title
xcopy/copy

Here's the main part of the batch file I want to convert, it's used to 
copy files to memory stick/backup location
add commands to itself based on adding commands for a new file
and compile several text files into one html page.

```

@echo off



rem settings



Title Compile web
Set Source=%USERPROFILE%\desktop\Source
Set server=%userprofile%\desktop\web server\unacquainted



rem Copy to USB



Echo copy to removable media? Yes or No
Set /p Answerremcopy=
Echo Temp > %answerremcopy%.tmp
IF EXIST y.tmp GOTO REMCOPYYEs
IF EXIST yes.tmp GOTO REMCOPYYEs
GOTO REMCOPYNO
:REMCOPYYES
del *.tmp
echo Drive letter to copy to?
set /p REMDRIVE=
xcopy "%userprofile%\desktop\backups\*.*" "%REMDRIVE%:\CompileBackup" /s /h /y
xcopy "%userprofile%\desktop\source\*.*" "%REMDRIVE%:\CompileBackup" /s /h /y
:REMCOPYNO
del *.tmp



rem Copy to local disk



xcopy "C:\documents and settings\samuel\desktop\backups\9\*.*" "C:\documents and settings\samuel\desktop\backups\10" /s /h /y /d
xcopy "C:\documents and settings\samuel\desktop\backups\8\*.*" "C:\documents and settings\samuel\desktop\backups\9" /s /h /y /d
xcopy "C:\documents and settings\samuel\desktop\backups\7\*.*" "C:\documents and settings\samuel\desktop\backups\8" /s /h /y /d
xcopy "C:\documents and settings\samuel\desktop\backups\6\*.*" "C:\documents and settings\samuel\desktop\backups\7" /s /h /y /d
xcopy "C:\documents and settings\samuel\desktop\backups\5\*.*" "C:\documents and settings\samuel\desktop\backups\6" /s /h /y /d
xcopy "C:\documents and settings\samuel\desktop\backups\4\*.*" "C:\documents and settings\samuel\desktop\backups\5" /s /h /y /d
xcopy "C:\documents and settings\samuel\desktop\backups\3\*.*" "C:\documents and settings\samuel\desktop\backups\4" /s /h /y /d
xcopy "C:\documents and settings\samuel\desktop\backups\2\*.*" "C:\documents and settings\samuel\desktop\backups\3" /s /h /y /d
xcopy "C:\documents and settings\samuel\desktop\backups\1\*.*" "C:\documents and settings\samuel\desktop\backups\2" /s /h /y /d
xcopy "C:\documents and settings\samuel\desktop\source\*.*" "C:\documents and settings\samuel\desktop\backups\1" /s /h /y /d



rem add file



echo Do you have a new file to add? yes or no
Set /p ANSWER=

Echo Temp >> %answer%.tmp

IF exist yes.tmp GOTO :1
IF exist y.tmp  GOTO :1

GOTO :4

:1

del %answer%.tmp

Echo type the file you wish to add, NOT including extension (.html, .txt)

Set /p NEW=



IF EXIST "%Source%\%New%.html" GOTO :2
IF EXIST "%Source%\%New%.txt" GOTO :3

Echo The file specified was not found, FAIL

Pause>nul
goto :1



:2

Echo Echo --------------------  >> compile.bat
Echo Echo Compiling %new%.html  >> compile.bat
Echo Echo --------------------  >> compile.bat


Echo Del "%%Server%%\%new%.html" >> compile.bat
Echo type "%%Source%%\html.txt" ^> "%%Server%%\%new%.html" >> compile.bat
Echo Type "%%Source%%\Head.txt" ^>^> "%%Server%%\%new%.html" >> compile.bat
Echo Type "%%Source%%\Body.txt" ^>^> "%%Server%%\%new%.html" >> compile.bat
Echo Type "%%Source%%\universal.txt" ^>^> "%%Server%%\%new%.html" >> compile.bat
Echo Type "%%Source%%\%new%.html" ^>^> "%%Server%%\%new%.html" >> compile.bat
Echo Type "%%Source%%\end.txt" ^>^> "%%Server%%\%new%.html" >> compile.bat
echo echo ..  >> compile.bat
echo echo ..  >> compile.bat
del %answer%.tmp
echo Another page to add?
set /p answer=
echo %answer% > %answer%.tmp
IF EXIST y.tmp goto :1
IF EXIST yes.tmp goto :1

GOTO :4



:3

Echo Echo --------------------  >> compile.bat
Echo Echo Compiling %new%.html  >> compile.bat
Echo Echo --------------------  >> compile.bat


Echo Del "%%Server%%\%new%.html" >> compile.bat
Echo Type "%%Source%%\html.txt" ^> "%%Server%%\%new%.html" >> compile.bat
Echo Type "%%Source%%\Head.txt" ^>^> "%%Server%%\%new%.html" >> compile.bat
Echo Type "%%Source%%\Body.txt" ^>^> "%%Server%%\%new%.html" >> compile.bat
Echo Type "%%Source%%\universal.txt" ^>^> "%%Server%%\%new%.html" >> compile.bat
Echo Type "%%Source%%\%new%.txt" ^>^> "%%Server%%\%new%.html" >> compile.bat
Echo Type "%%Source%%\end.txt" ^>^> "%%Server%%\%new%.html" >> compile.bat
echo echo ..  >> compile.bat
echo echo ..  >> compile.bat

del %answer%.tmp
echo Another page to add?
set /p answer=
echo continue > %answer%.tmp
IF EXIST y.tmp goto :1
IF EXIST yes.tmp goto :1


GOTO :4



rem compile



:4
Del %answer%.tmp

Echo --------------------
Echo Compiling Index.html
Echo --------------------


Del "%Server%\index.html"
type "%source%\html.txt" > "%Server%\index.html"
Type "%Source%\Head.txt" >> "%Server%\index.html"
Type "%Source%\Body.txt" >> "%Server%\index.html"
Type "%Source%\universal.txt" >> "%Server%\index.html"
Type "%Source%\index.txt" >> "%Server%\index.html"
Type "%Source%\end.txt" >> "%Server%\index.html"
```

I basically want something that does the same effect and want to LEARN the same commands and how to use them, maybe anything that would be more effective considering how much more powerful the terminal is supposed to be?

Oh, and to add permissions to everything so that the server doesn't have permission troubles, but I'm guessing I should just add a chmod -R 777 command?

html directory is now Home/User/Public/Web_server with 777 permissions throughtout
text file directory is Home/User/Documents with whatever permissions are on as install.

I REALLY don't want to go back to copy-pasting through all pages again :(

Help appreciated...

---

### Post by ironic.demise on 2010-05-05
Nobody at all know how I can do this, Just saw that a "read" is like a "set" and the variable is prefixed with a $? is this correct?

Found that redirects work the same (< << > >>)

CD along with echo are the same...

del is rm
Title is not nexessary, as is @echo off (though I'd prefer them)

comment out works with //

copy is copy?

What of IF EXIST GOTO?
What of type? :edit: Cat :D

---

### Post by Old *ix Geek on 2010-05-05
You need to understand that there is NOTHING *nix can't do in a script that windoze can. For every one shell command (or whatever they're called in the M$ world), there are probably 100 shell commands in *nix--AND, because every *nix command has a plethora of arguments--which can be combined--every command ends up with more possibilities than you'd ever imagine. That's why the *nix shell is so powerful, and scripting with it is so much more elegant than what's possible with windows.

All you need is a book/guide/tutorial on basic UNIX/Linux shell scripting; make sure you're looking at info for Bourne or bash shells.

Since I don't know what most of those M$ commands in your script mean, I can't help you translate them to *nix.

---

### Post by ironic.demise on 2010-05-05
> **Old *ix Geek said:**
> You need to understand that there is NOTHING *nix can't do in a script that windoze can. For every one shell command (or whatever they're called in the M$ world), there are probably 100 shell commands in *nix--AND, because every *nix command has a plethora of arguments--which can be combined--every command ends up with more possibilities than you'd ever imagine. That's why the *nix shell is so powerful, and scripting with it is so much more elegant than what's possible with windows.

All you need is a book/guide/tutorial on basic UNIX/Linux shell scripting; make sure you're looking at info for Bourne or bash shells.

Since I don't know what most of those M$ commands in your script mean, I can't help you translate them to *nix.

I believe that 

cat = type
cp = copy/xcopy
read = set
if = (better than) if exist goto
< << > >> | = < << > >> | 
// = rem
rm = del
echo = echo

As for @echo off and title... well in windows they didn't do anything at all really... they just changed the visual output from everything to nothing and changed the name of the window...

I've found each windows command and it's closest ubuntu equivalent on these forums and now only need to understand each better, which I intend to do with a man page.

Thankyou for your help, I think you underestimate windows just a little bit though... I know Microsoft want you to stay inside their little box and they didn't give much freedom... but I spent the past few years seeing what I could do when Microsoft wouldn't let me... Now I pushed it as far as I think it will go I turn to Ubuntu for a bit more oomph! in sheer capability.

That said... Windows can do a lot through CMD... It's worth learning it just to get around Admins at public areas.


Windows is the most commonly used OS and also... has the most powerless admins...

I remember the only admin I ever knew to use Linux... and the only Admin I've ever known to be able to keep the rules enforced on the computers!

---

### Post by Old *ix Geek on 2010-05-05
I've replied in your newer thread and am really happy to see that you're making great progress.

> **ironic.demise said:**
> I think you underestimate windows just a little bit though... I know Microsoft want you to stay inside their little box and they didn't give much freedom... but I spent the past few years seeing what I could do when Microsoft wouldn't let me... Now I pushed it as far as I think it will go I turn to Ubuntu for a bit more oomph! in sheer capability.

That said... Windows can do a lot through CMD...Not wanting to start a war here, but I tell you what: Grab yourself a copy of a UNIX shell scripting book such as [Mastering UNIX Shell Scripting]("http://www.amazon.com/Mastering-Unix-Shell-Scripting-Administrators/dp/0470183012/ref=pd_sim_b_1") (1032 pages) or [Linux Command Line and Shell Scripting Bible]("http://www.amazon.com/Linux-Command-Shell-Scripting-Bible/dp/047025128X/ref=pd_sim_b_1") (840 pages), take a couple months to really learn their contents, and then come back and we'll see how your opinion of "Windows can do a lot through CMD" has changed, okay? :lolflag: Seriously, once you're aware of the power of the *nix shell, you'll realize just how lacking the M$ equivalent truly is.

---

