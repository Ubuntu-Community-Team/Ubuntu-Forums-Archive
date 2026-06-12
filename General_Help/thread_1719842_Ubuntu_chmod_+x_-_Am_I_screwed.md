---
title: "Ubuntu chmod +x - Am I screwed?"
date: 2011-04-02
forum: General Help
---

### Post by Iskallfan on 2011-04-02
First off, i just started using Ubuntu so i'm a real newbie but anyways cheers for that, i must say i really like ubuntu so far and enjoy it to 100% !

To day i was trying to chmod a file, followed a guide on how you could do that but it didn't end up like i wanted to so im now wondering if the changes ive made is a / can be a security issue?

Here is my term log.
```
 iskallfan@GA-73PVM-S2H:~$ locate tekstfile chmod +x tekstfile
/bin/chmod
/usr/lib/perl/5.10.1/auto/POSIX/chmod.al
/usr/share/icons/Humanity/mimes/128/gnome-mime-application-xhtml+xml.svg
/usr/share/icons/Humanity/mimes/16/gnome-mime-application-xhtml+xml.svg
/usr/share/icons/Humanity/mimes/16/image-x-svg+xml.svg
/usr/share/icons/Humanity/mimes/22/application-atom+xml.svg
/usr/share/icons/Humanity/mimes/22/application-rss+xml.svg
/usr/share/icons/Humanity/mimes/22/gnome-mime-application-atom+xml.svg
/usr/share/icons/Humanity/mimes/22/gnome-mime-application-rss+xml.svg
/usr/share/icons/Humanity/mimes/22/gnome-mime-application-xhtml+xml.svg
/usr/share/icons/Humanity/mimes/22/image-x-svg+xml.svg
/usr/share/icons/Humanity/mimes/24/application-atom+xml.svg
/usr/share/icons/Humanity/mimes/24/application-rss+xml.svg
/usr/share/icons/Humanity/mimes/24/gnome-mime-application-atom+xml.svg
/usr/share/icons/Humanity/mimes/24/gnome-mime-application-rss+xml.svg
/usr/share/icons/Humanity/mimes/24/gnome-mime-application-xhtml+xml.svg
/usr/share/icons/Humanity/mimes/24/image-x-svg+xml.svg
/usr/share/icons/Humanity/mimes/32/gnome-mime-application-xhtml+xml.svg
/usr/share/icons/Humanity/mimes/48/application-atom+xml.svg
/usr/share/icons/Humanity/mimes/48/application-rss+xml.svg
/usr/share/icons/Humanity/mimes/48/gnome-mime-application-atom+xml.svg
/usr/share/icons/Humanity/mimes/48/gnome-mime-application-rss+xml.svg
/usr/share/icons/Humanity/mimes/48/gnome-mime-application-xhtml+xml.svg
/usr/share/icons/Humanity/mimes/48/image-x-svg+xml.svg
/usr/share/icons/Humanity/mimes/64/gnome-mime-application-xhtml+xml.svg
/usr/share/icons/gnome/16x16/mimetypes/gnome-mime-application-xhtml+xml.png
/usr/share/icons/gnome/22x22/mimetypes/gnome-mime-application-xhtml+xml.png
/usr/share/icons/gnome/24x24/mimetypes/gnome-mime-application-xhtml+xml.png
/usr/share/icons/gnome/256x256/mimetypes/gnome-mime-application-xhtml+xml.png
/usr/share/icons/gnome/32x32/mimetypes/gnome-mime-application-xhtml+xml.png
/usr/share/icons/gnome/48x48/mimetypes/gnome-mime-application-xhtml+xml.png
/usr/share/man/man1/chmod.1.gz
/usr/share/man/man2/chmod.2.gz
/usr/share/man/man2/fchmod.2.gz
/usr/share/man/man2/fchmodat.2.gz
/usr/share/mime/application/atom+xml.xml
/usr/share/mime/application/docbook+xml.xml
/usr/share/mime/application/mathml+xml.xml
/usr/share/mime/application/metalink+xml.xml
/usr/share/mime/application/rdf+xml.xml
/usr/share/mime/application/rss+xml.xml
/usr/share/mime/application/vnd.google-earth.kml+xml.xml
/usr/share/mime/application/vnd.mozilla.xul+xml.xml
/usr/share/mime/application/x-fictionbook+xml.xml
/usr/share/mime/application/xhtml+xml.xml
/usr/share/mime/application/xslt+xml.xml
/usr/share/mime/application/xspf+xml.xml
/usr/share/mime/image/svg+xml-compressed.xml
/usr/share/mime/image/svg+xml.xml
/usr/share/mime/text/x-opml+xml.xml
```

Regards /Dennis

---

### Post by Enigmapond on 2011-04-02
Firstly, welcome to the forum! Can you be a bit more specific as to exactly that you are trying to do?

---

### Post by Iskallfan on 2011-04-02
> **Enigmapond said:**
> Firstly, welcome to the forum! Can you be a bit more specific as to exactly that you are trying to do?

Thank you, it seems to be a really nice community!
Alright, here we go.

I want to execute a .bat file, and as far as i know windows bat files are obviously not supported so i created a new file, just a file and in this file i placed all the information who was in the .bat file.
Now i wanted to chmod this file to make it executable, but then it didn't really end up as i wanted to as you can see in the log i posted. 

Im also wondering if the command i ran can cause my system to be unstable etc?

Sorry for my bad english.

Edit: If this helps, i want to install the bot client from [http://www.powerbot.org/vb/](http://www.powerbot.org/vb/).
But it comes with an .bat install script.

Regards /Dennis

---

### Post by WorMzy on 2011-04-02
If the command you ran was ```
locate tekstfile chmod +x tekstfile
```

Then all you've done is search for files with names like "tekstfile", "chmod" and "+x". It's a harmless command.

This bot that you're trying to install, if it's using a .bat to install itself, then it's probably for Windows only.

---

### Post by Enigmapond on 2011-04-02
By just renaming a .bat file and trying to execute it, will not work. Is this part of a game or something? Do you have Wine installed? What is this file for? I don't think you compromised security with what you did.

---

### Post by Iskallfan on 2011-04-02
> **WorMzy said:**
> If the command you ran was ```
locate tekstfile chmod +x tekstfile
```Then all you've done is search for files with names like "tekstfile", "chmod" and "+x". It's a harmless command.

This bot that you're trying to install, if it's using a .bat to install itself, then it's probably for Windows only.
Yea that's the command i ran, ok glad to hear that!
I think it's for windows, but is there a way to run the .bat file and install the bot client?

> **Enigmapond said:**
> By just renaming a .bat file and trying to execute it, will not work. Is this part of a game or something? Do you have Wine installed? What is this file for? I don't think you compromised security with what you did.
It's an bot client for a game, runescape (java based online game).
I have wine installed, but it can't run .bat files or can it?
The file is an installation script, see the code below.

Glad to hear that! :p

This is what the install.bat script contains
```
@ECHO OFF 
 
SET cc=javac 
SET cflags= 
SET src=src 
SET lib=lib 
SET res=resources 
SET out=bin 
SET dist=RSBot.jar 
 
CALL :clean 2>NUL 
CALL "%res%\FindJDK.bat" 
 
SET lstf=temp.txt 
SET imgdir=%res%\images 
SET manifest=%res%\Manifest.txt 
SET versionfile=version.txt 
FOR /F %%G IN (%versionfile%) DO SET version=%%G 
SET scripts=scripts 
 
ECHO Compiling bot 
IF EXIST "%lstf%" DEL /F /Q "%lstf%" 
FOR /F "usebackq tokens=*" %%G IN (`DIR /B /S "%src%\*.java"`) DO CALL :append "%%G" 
IF EXIST "%out%" RMDIR /S /Q "%out%" > NUL 
MKDIR "%out%" 
"%cc%" %cflags% -d "%out%" "@%lstf%" 2>NUL 
DEL /F /Q "%lstf%" 
 
:scripts 
ECHO Compiling scripts 
ECHO. > "%scripts%\.class" 
DEL /F /Q "%scripts%\*.class" > NUL 
"%cc%" %cflags% -cp "%out%" %scripts%\*.java 
 
ECHO Packing JAR 
 
IF EXIST "%dist%" DEL /F /Q "%dist%" 
IF EXIST "%lstf%" DEL /F /Q "%lstf%" 
COPY "%manifest%" "%lstf%" 
ECHO Specification-Version: "%version%" >> "%lstf%" 
ECHO Implementation-Version: "%version%" >> "%lstf%" 
jar cfm "%dist%" "%lstf%" -C "%out%" . %scripts%\*.class %res%\version.dat %imgdir%\* %res%\*.bat %res%\*.sh 
DEL /F /Q "%lstf%" 
 
:end 
CALL :clean 2>NUL 
ECHO Compilation successful. 
GOTO :eof 
 
:append 
SET gx=%1 
SET gx=%gx:\=\\% 
ECHO %gx% >> %lstf% 
GOTO :eof 
 
:clean 
RMDIR /S /Q "%out%" 
DEL /F /Q %scripts%\*.class 
GOTO :eof
```

---

### Post by pastalavista on 2011-04-02
never mind

---

### Post by Enigmapond on 2011-04-02
Well if you have wine, right click the bat file and try loading it to Wine....if it can't then it will probably only work with windoze... Sorry I can't be of any further help.

---

### Post by MacinViLLe on 2011-04-02
[LEFT]Maybe it didn't end up well because the installer you're trying to run isn't compiled to run for Ubuntu? Have you done what you did by following a tutorial for example? If it is supposed to run on Windows, then use Wine to run the program (though it is not an assurance that everything will run accordingly, simple because the installer might not be designed for Ubuntu).
[/LEFT]

---

### Post by WorMzy on 2011-04-02
> **Iskallfan said:**
> Yea that's the command i ran, ok glad to hear that!
I think it's for windows, but is there a way to run the .bat file and install the bot client?


It's an bot client for a game, runescape (java based online game).
I have wine installed, but it can't run .bat files or can it?
The file is an installation script, see the code below.

Clicking the download link on that forum you posted gives me a RSBot-232.jar, is this the bot you're trying to install? If so, you don't need to "install" it, you just run it with Java.

```
java -jar RSBot-232.jar
```

Here's a screenshot of it running on my machine.

[[IMG]http://img651.imageshack.us/img651/8462/201104021726231920x1080.th.png[/IMG]](http://img651.imageshack.us/img651/8462/201104021726231920x1080.png)

---

### Post by Iskallfan on 2011-04-02
> **WorMzy said:**
> Clicking the download link on that forum you posted gives me a RSBot-232.jar, is this the bot you're trying to install? If so, you don't need to "install" it, you just run it with Java.

```
java -jar RSBot-232.jar
```Here's a screenshot of it running on my machine.

[[IMG]http://img651.imageshack.us/img651/8462/201104021726231920x1080.th.png[/IMG]]("http://img651.imageshack.us/img651/8462/201104021726231920x1080.png")

Yea that's the bot i try to install, but i can't get it to work.
Do i have to type in the command in the terminal or can i just right click the file, and run it with java jre 6?

---

### Post by WorMzy on 2011-04-02
Either should work.

---

### Post by Iskallfan on 2011-04-03
> **WorMzy said:**
> Either should work.
Can't get it to work nor can i launch java applets. 
Ive installed Java JRE, Java JDK and the java plugin.

---

### Post by WorMzy on 2011-04-03
Which JRE? Sun/Oracle's or OpenJDK's?

I'm using Oracle's.


This may help you install it: [http://www.liberiangeek.net/2010/10/sun-java-runtime-jre-ubuntu-10-10-maverick-meerkat-partner-repository/](http://www.liberiangeek.net/2010/10/sun-java-runtime-jre-ubuntu-10-10-maverick-meerkat-partner-repository/)

---

