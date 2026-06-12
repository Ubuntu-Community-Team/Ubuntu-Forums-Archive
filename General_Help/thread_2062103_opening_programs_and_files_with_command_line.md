---
title: "opening programs and files with command line"
date: 2012-09-24
forum: General Help
---

### Post by arnicainthemembrane on 2012-09-24
Hi, I'm trying to figure out how to us the CLI more effectively. 

GUIs are so useful to me because all the information I need is right in front of me. I see a characteristic widget, click on it and open the program.

With the CLI I find I have to already know what to type in order to access a given program- either that or I'm not looking in the right area. 

For example, I know I can type "firefox" to open the firefox web browser. But I only know how to do this because I watched someone else do it. With other programs it is hit and miss. Often simply typing the name of the program into the terminal won't open it because that's not the right command.

What I don't get is, how does one a. know what programs are available for use via the CLI and b. know what command line prompts will open those programs and then c. use the command line to open certain files with certain applications?

And please don't just direct me to the man pages, they aren't really helping for such basic functions...


thanks!

---

### Post by dcstar on 2012-09-24
> **arnicainthemembrane said:**
> ..........
What I don't get is, how does one a. know what programs are available for use via the CLI
..........


You go into Synaptic and look at the Properties of the installed package and see what is installed in the "bin" folders, or you copy the Launcher to your desktop and see what it launches.

---

### Post by Lars Noodén on 2012-09-24
You can get a reasonably thorough list of what apps your system has with this script.

```

for i in /bin/ /sbin/ /usr/bin/ /usr/sbin/ /usr/local/bin/ /usr/local/sbin/;
do (for j in $(ls "$i"); 
  do man $j | head -n 7 | grep ' - ' | sed -e 's/^ *//';done);
done| sort -u > ~/myapps

```

Then you can browse the output with [less](http://manpages.ubuntu.com/manpages/precise/en/man1/less.1.html)

```

less ~/myapps

```

You can then get the full instructions on any specific program using [man](http://manpages.ubuntu.com/manpages/precise/en/man1/man.1.html)

```

# e.g.
man ls

```

Can you elaborate on what you mean by "c. use the command line to open certain files with certain applications" ?  There's gnome-open which will take a guess at which graphical application to open in order to use a certain file.

---

### Post by arnicainthemembrane on 2012-09-24
Thanks for the advice, that helps me with half the problem. However I don't get how I can know what programs I've got, and how to open them, using the CLI alone.

---

### Post by arnicainthemembrane on 2012-09-24
"Can you elaborate on what you mean by "c. use the command line to open certain files with certain applications" ? There's gnome-open which will take a guess at which graphical application to open in order to use a certain file."

With a GUI all I have to do to say, open a document is  left click on the widget and open it with the default application, or right click to choose an application.

I'm wondering how I can do this using the CLI. I am capable of finding the file itself but have no idea how to open it using a given program. 

thanks

---

### Post by shreepads on 2012-09-24
Qn a. All apps can be initiated from command line. Of course if the app requires a window you must have a window manager running. Pure command line apps don't need this.

Qn b. Open Nautilus and browse to /usr/share/applications. Look at the files named *.desktop and identify the one for the app you need and open it in Gedit. Find the line 'Exec=<appname>'. That bit is what you can use to trigger the app from command line.

Qn c. No straight answer, you need to look at the man page for the given app to understand it's command line input params

---

### Post by 3rdalbum on 2012-09-24
> **arnicainthemembrane said:**
> "Can you elaborate on what you mean by "c. use the command line to open certain files with certain applications" ? There's gnome-open which will take a guess at which graphical application to open in order to use a certain file."

With a GUI all I have to do to say, open a document is  left click on the widget and open it with the default application, or right click to choose an application.

I'm wondering how I can do this using the CLI. I am capable of finding the file itself but have no idea how to open it using a given program. 

thanks

<program> <filepath>

For instance, to open a file on your desktop called "hello.html", using Firefox:

```
firefox /home/arnicainthemembrane/Desktop/hello.html
```

As mentioned before, you can use Synaptic Package Manager to find the actual name of the program; Synaptic is not preinstalled, but you can install it using Ubuntu Software Center. Once Synaptic is installed, open it and select a package. Right-click it and choose Properties, then go to the Installed Files tab. Any files inside a /bin/ folder are programs you can run.

Another little tip for using the command-line: You don't have to type file paths into the terminal. You can drag a file into the terminal to input its path. Quick and easy for those rare times you absolutely need a terminal.

---

### Post by einonm on 2012-09-24
The keyword 'apropos' is also very useful when searching for programs, for example, 'apropos file' gives you a list of programs that relate to handling files (there are a lot for that particular example!). 'apropos web' is another good example for getting web related programs.

Also using the <TAB> key gives a list of matching commands for a partially entered program name, e.g. :
```
:~$ fi <TAB>
fi           fig4latex    file         file-roller  find2perl    findfs       findmnt      firefox      
fiascotopnm  filan        filefrag     find         findaffix    findhyph     findsmb      fitstopnm

```

---

### Post by drmrgd on 2012-09-24
I'd also recommend you have a look at the command line utility called "apropos".  This utility will search the system for installed packages that match a search query.  For example:

```
$ apropos web
feh-cam (1)          - a utility for viewing live webcam images
firefox (1)          - a free and open source web browser from Mozilla                                                     
gen_cam_menu (1)     - a utility for viewing live webcam images                                                            
google-chrome (1)    - the web browser from Google                                                                         
loweb (1)            - LibreOffice office suite                                                                            
LWP (3pm)            - The World-Wide Web library for Perl                                                                 
lwp-download (1p)    - Fetch large files from the web                                                                      
LWP::RobotUA (3pm)   - a class for well-behaved Web robots
LWP::UserAgent (3pm) - Web user agent class
rekonq (1)           - A lightweight Web Browser for KDE based on WebKit
sensible-browser (1) - sensible editing, paging, and web browsing
sensible-editor (1)  - sensible editing, paging, and web browsing
sensible-pager (1)   - sensible editing, paging, and web browsing
wsgen (1)            - Java(TM) API for XML Web Services (JAX-WS) 2.0
wsimport (1)         - Java(TM) API for XML Web Services (JAX-WS) 2.0
```

That query returned all packages that have something to do with my query "web".  From there, I can use the man pages for each package to see how to use it fully to know if it'll work for what I want.  That will help you figure out what packages are available for specific tasks.

---

### Post by arnicainthemembrane on 2012-09-24
awesome. thanks for the advice.

---

### Post by zombifier25 on 2012-09-24
Just to add, for example you need to open a file with the default application associated to that file:
```
xdg-open filename
```

---

