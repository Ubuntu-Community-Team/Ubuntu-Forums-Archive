---
title: "where do applications install to and what are these folders in root?"
date: 2010-10-12
forum: General Help
---

### Post by fuzzylogic25 on 2010-10-12
I am trying to locate the file VUZE. its an executable of a torrent file i believe but couldnt find it in /home/john/.azureus/ where i would expect it to be.

Where else could it be?

Also, what are these folders and what do they contain:
bin
boot
dev
home
lib
opt
proc
root
sbin
srv
sys
tmp
usr

is there somewhere where i can read about this. One of the things that confuses me is what all these folders do. I always thought applications installed to /home/john/.X where X is the application name but then sometimes ive seen files in /opt and /usr/... so now im really getting confused!

---

### Post by Chesamo on 2010-10-12
By default, most programs are installed into /bin, /usr/bin, /usr/share/bin, or /opt. I'm not entirely sure of the difference between the directories, perhaps someone with more experience can shed some light on this.

In order:
/bin holds the default executables (basic terminal apps, like ls and cat)
/boot holds the GRUB bootloader configuration
/dev contains development libraries (I believe)
/home contains all of the users home directories
/lib contains the precompiled libraries that applications can use (like libc, etc.)
/opt contains more programs, usually commercial programs
/proc Don't know
/root The root user's home directory
/sbin Don't know
/srv Don't know
/sys Don't know
/tmp temporary files
/usr Lots of stuff, libraries, binaries, source files for development

Two you excluded:
/var Variable information, data that changes a lot (Apache, for example, installs into here by default)
/etc Most system configuration

/home/john/.* is the location of the *configuration files* for that particular program. Unless you manually install a program (which is unlikely for most new Linux users), you will rarely see binary files in ~/.* directories.

Why do you need to find the executable file itself? 99 times out of 100 if you need to link it, you can just use the Terminal command associated with the program.

---

### Post by fuzzylogic25 on 2010-10-12
Well its a java file I believe or a shell script file. Basically, Vuze is a java program and its gui is VERY slow. Scrolling down files in the program is really slow and I came across this link which aims to fix it:

[http://ubuntuforums.org/archive/index.php/t-1129187.html](http://ubuntuforums.org/archive/index.php/t-1129187.html)

I shall paste the main part of that link here:

===========================================

Step 1)
Rightclick the shortcut, open its properties and find out where the corresponding 
shell script is. In my case it's /opt/vuze/vuze.

Step 2)
Open the script in an editor. Let's assume your editor is gedit: Push ALT+F2,
type "gedit /opt/vuze/vuze" (without the quotes) and confirm by pushing enter.

Step 3)
You examine the script and find this at its end
${JAVA_PROGRAM_DIR}java "${JAVA_ARGS}" \
-cp "${CLASSPATH}" \
-Djava.library.path="${PROGRAM_DIR}" \
-Dazureus.install.path="${PROGRAM_DIR}" \
-Dazureus.script="$0" \
$JAVA_PROPS \
$START_CLASS "$@"
Now you change the code to

${JAVA_PROGRAM_DIR}java "${JAVA_ARGS}" \
-cp "${CLASSPATH}" \
-Djava.library.path="${PROGRAM_DIR}" \
-Dsun.java2d.opengl=true \
-Dazureus.install.path="${PROGRAM_DIR}" \
-Dazureus.script="$0" \
$JAVA_PROPS \
$START_CLASS "$@"

===================================================

So I am trying to find that /opt/vuze/vuze but I dont have a /opt/vuze folder so I dont know where it might be.

---

