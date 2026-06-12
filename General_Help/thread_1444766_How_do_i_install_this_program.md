---
title: "How do i install this program?"
date: 2010-04-01
forum: General Help
---

### Post by ep1centre on 2010-04-01
**How do i install this program?**             
                                                                How do i Install a tar.gz file?

Now i know a tar.gz file is like a zip file in windows but when i extracted it theres a folder with a few files in it including some instructions on how to install the program but to be honest i'm useless when it comes to using terminal and i dont know how to get the "install file running".

The instructions read :



Provided your GNU/Linux distribution doesn't include logkeys package in its
repositories, manual installation of logkeys from source is as easy as:

 $ tar xvzf logkeys-0.1.0.tar.gz      # to extract the logkeys archive
 
 $ cd logkeys-0.1.0/build     # move to build directory to build there
 $ ../configure               # invoke configure from parent directory
 $ make                       # make compiles what it needs to compile
 ( become super&#8601;user now )    # you need root to install in system dir
 # make install               # installs binaries, manuals and scripts

That's it. If everything went through fine (as it mostly should, I think), you
can probably skip ahead to the next section now.

To ever uninstall logkeys, remove accompanying scripts and manuals, issue

 # make uninstall    # in the same logkeys-0.1.0/build dir from before

To install the binaries in path other than /usr/local/bin, use configure with
--prefix switch, for example:

 $ ../configure --prefix=/usr

Along with other standard configure options, you can also use:

 $ ../configure --enable-evdev-path=PATH

to have logkeys look for input event devices in PATH ( $(PATH)/eventX ) instead
of preconfigured default /dev/input (/dev/input/eventX), and

 $ ../configure --enable-evdev=DEV

to have logkeys define static event device DEV (i.e. /dev/input/eventX) instead
of looking for it in default /dev/input path or custom evdev-path.

The input event device we are referring to, here, is the kernel event interface
echoing keyboard events. If using either of these two --enable-evdev*
switches, make sure you provided correct PATH/DEV.

A copy of these instructions is in the accompanying INSTALL file.





help would be very much appreciated!

Thank you.

---

### Post by NCLI on 2010-04-01
1. We don't really care why you want this software, keep it out of the support forum. If anything, it is a subject for the Community Café.

2. Here's what you need to do:

Open a terminal(Applications->Accesories->Terminal).

Run

```
cd logkeys-0.1.0/build
```
then run
```
../configure
```
then
```
make
```
then
```
sudo make install
```
The last part will ask for your password. Just enter your user password, don't worry about no symbols appearing as you type, this is a security precaution.

It should now be installed.

---

### Post by jaco223 on 2010-04-01
login to your terminal as superuser. type su then hit enter. go to the directory where you have your file,
type ./configure. after that completes type make. after that type make install.

Hope this helps

Jaco

---

### Post by ep1centre on 2010-04-01
Thank you for your replies i've now installed the program it was simple and seemed to go flawlessly however according to these instructions there should 2 scripts in bin/lkl and bin/lklk to stop start the program but i cannot find it there, also is there a simple way (like add a command somewhere) to have it start up when ubuntu starts up (ie without it having to manually start it each time)?



3. Usage how-to
===============================================================================

logkeys is simple. You can either invoke it directly, by typing full command 
line, or use the provided scripts. There are two scripts in this package:

 bin/lkl  , which starts the logkeys daemon, and
 bin/lklk , which kills it.

You can use these two scripts for starting and stopping the keylogger quickly
and covertly. You can modify the scripts as you like.
Note that logkeys is installed setuid, so the root password need not be
provided at runtime.

Default log file is /var/log/logkeys.log and is not readable by others.

I suggest you first test the program manually with

 $ touch test.log
 $ logkeys --start --output test.log

and in the other terminal follow it with

 $ tail --follow test.log

and see if the pressed keys match to those noted. If you use a US keyboard
layout, use -u switch. Make sure your terminal character locale is set to UTF-8

 $ locale
 LANG=xx_YY.UTF-8
 LC_CTYPE="xx_YY.UTF-8"
 ...

or alternatively, you need en_US.UTF-8 locale available on your system

 $ locale -a
 ...
 en_US.UTF-8
 ...

otherwise you will only see odd characters (like &#42102;) when pressing character
keys.

It is very likely that you will see only some characters recognized, without
any hope for Shift and AltGr working even slightly correct, especially when
starting logkeys in X. In that case it is better to switch to virtual terminal, 
e.g. tty4 (Ctrl+Alt+F4), and there execute:

 $ logkeys --export-keymap my_lang.keymap

Then open my_lang.keymap in UTF-8 enabled text editor and manually repair any
missing or incorrectly determined mappings. From then on, execute logkeys by

 $ logkeys --start --keymap my_lang.keymap

Again, see if it now works correctly (character keys appear correct when you
are viewing the log file in editor), and opt to modify bin/lkl starter script.

logkeys acts as a daemon, and you stop the running logger process with

 $ logkeys --kill

(or bin/lklk provided script).

For more information about logkeys log file format, logkeys keymap format, and
command line arguments, read the application manual,

 $ man logkeys

or see the wiki at project website: [http://code.google.com/p/logkeys/](http://code.google.com/p/logkeys/)

If you create full and completely valid keymap for your particular language,
please upload it to website or send it to me by e-mail. Thanks.

Abuse the output of this software wisely.




The 1st paragraph makes sense about the scripts but the rest unfortunatly goes over my head, any more help would be greatly apreciated!

Also i apologize for having posted my reasons for wanting the software i just didn't want to stir up an argument over the reasons why i might be requesting help to install software with such potential for illegal activities, i have now edited my post and I'll keep in mind to keep further requests for help on here short and straight to the point!

Thank you.

---

### Post by NCLI on 2010-04-01
They're probably in /usr/bin. To run a program located in /usr/bin, simply press Alt+F2, then type the name of the program in the box which will pop up, and press enter.

In this case, you should input lkl to start the service, and lklk to stop it.

---

### Post by ep1centre on 2010-04-02
Thanks for the reply, i've tryed that and it may have worked or not, i dont get any confirmation and i dont know how to check whether the program is running, all i can hear after pressing alt+F2 and typing lkl is a quick bit of hard drive activity and that's it.

I still don't know where the Logs are actually kept so i don't know whether its even working?!?

Any further help is very much appreciated.

---

### Post by ep1centre on 2010-04-03
Anyone? 

It'd be very much apreciated!

---

### Post by louis--taylor on 2010-04-03
try looking at [http://code.google.com/p/logkeys/wiki/Documentation](http://code.google.com/p/logkeys/wiki/Documentation)
or [http://lmgtfy.com/?q=logkeys+ubuntu](http://lmgtfy.com/?q=logkeys+ubuntu)

To run on startup you could either edit the accompanying bin/lkl script, or copy the whole line you want logkeys issued with, e.g. logkeys --start --keymap /home/I/mylang.map 
then add this line (or just lkl without quotes if you edited the lkl script beforehand) to your */etc/rc.local* (or */etc/rc.d/rc.local* or similar file) before the exit 0 call. Alternatively, you could use your desktop's "autorun manager" to, again, run that command line or script. 
 
      
(taken from logkeys' wiki)

---

