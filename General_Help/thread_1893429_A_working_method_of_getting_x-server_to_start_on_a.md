---
title: "A working method of getting x-server to start on a headsless unit?"
date: 2011-12-10
forum: General Help
---

### Post by davegurn on 2011-12-10
Hi 

i know theres alot of discussion on this but alot of methods are old and out-dated. i want to use the gui desktop remotely on a vps server that i have purchased and obviously i do not have access to the unit and it is headless so xserver will not start.

I have already tried the vnc method but the desktop is very laggy and forwarding x over ssh is not for me either as would like to use the desktop as if i am sat in front of it. I know alot of people flame you saying what you want to do that for, command line is king! but i purchased this vps with the intention of using it like a normal desktop and file sharing.

So i am under the impression that rdp will be the least laggy but requires x to be started on the server before i acces it. but by default x will not start on a headless unit.

i am using ubuntu oneric, does anyone no a current workaround for this?

Thanks for any help

---

### Post by tomdkat on 2011-12-10
You don't need to run the X server on the headless system since you won't be displaying anything on the headless system, itself (since it's headless).  You can run XDM and use XDMCP to gain graphical access to your system over the network (or the Internet if things are setup correctly).

I've done this with HP-UX, Solaris, and Linux systems and it works well.  Don't expect it to be fast or anything but it should be usable.

Since you already tried VNC and found the performance unacceptable, using XDMCP might not perform any better for you.

Keep in mind you WILL need an X server running on the client system you'll be using to remotely operate the Linux system in question.

Peace...

---

### Post by davegurn on 2011-12-10
Ok thanks for the suggestion tomdkat

to be honest i dont really know how to do what your saying or what it is as linux is a foreign language to me and im now starting to realize how spoon fed i really was with windows.

I can only really do basic tasks and things that ive found tutorials for (hence why i want to use the gui)

maybe iyl just have to put up with vnc

---

### Post by davegurn on 2011-12-15
Just for anyone whose interested i tried "freenx server" and that was still very laggy with the gui. i understand i have a rubbish connection (1-1.6mb) and was about to give up when i found the "x2go server" and it knocks vnc and freenx out of the park, its almost like im sat in front of computer and i don't think i could get it any smoother with my 1mb connection. (these instructions are confirmed working on ubuntu oneric)
[B][COLOR=Red]
(Edit: it was running smoothly with lxde but when i tried gnome it was still very laggy but i think its just my 1mb connection isn't enough to run gnome smoothly remotely so if your connection is anything like mine then i suggest you go with lxde and if you have a fast connection then gnome should run smoothly with sound, file transfer and printing! I can confirm that x2go transferred sound with its default settings but my connection is to slow to transfer it smoothly!)[/COLOR][/B]

to install the "x2go server" on the machine you want to connect to first make sure you have an ssh server installed ie "openssh server" 
**sudo apt-get install openssh-server**

and then follow the instructions below.

**sudo apt-add-repository ppa:x2go/stable** (if this doesn't work you need to run this first
**sudo apt-get install python-software-properties**)
[B]sudo apt-get update
sudo apt-get install x2goserver[/B]
**sudo apt-get install x2gognomebindings** # if you use GNOME
**sudo apt-get install x2golxdebindings**  # if you use LXDE/lubuntu

(the above commands are fine and your ready to connect for gnome or lxde but if you want to see all available x2go components then type **sudo apt-cache search x2go**)

then if you want to connect to the server from windows then simply download the "x2go windows client" from their website [[COLOR=Blue]**here**[/COLOR]]("http://www.x2go.org/index.php?id=7&L=5")

or if you want to connect to it from another ubuntu computer then install the "x2go client" with these commands.

**sudo apt-add-repository ppa:x2go/stable **(if this doesn't work you need to run this first
s**udo apt-get install python-software-properties**)

[B]sudo apt-get update
sudo apt-get install x2goclient[/B]

Then open the x2go client and enter a name for your session next to **[COLOR=Blue]Session name[/COLOR]**. 
Then the ip address of the server you want to connect to for [B][COLOR=Blue]host. [COLOR=Black]
[/COLOR][/COLOR][/B]The user you want to use to login to the server for [COLOR=Blue]**Login**[/COLOR] [COLOR=Black]ie root
and select your session type ie [COLOR=Blue][B]GNOME.
[/B][COLOR=Black]Click connection and select your internet type.[/COLOR][COLOR=Black]Then click ok and you will see a white box with the session name and details you entered, click the box and the login screen will pop up, then just enter the password for the user on the server you selected and press ok and then it will login with that user and launch a gui session.

If you want the sound tra[/COLOR][/COLOR][/COLOR][COLOR=Black][COLOR=Blue][COLOR=Black]nsfer of x2go to work on lxde you need to install PulseAudio, i used this command
[/COLOR][/COLOR][/COLOR]**sudo apt-get install pulseaudio pavucontrol**

and i installed the software center

**sudo apt-get install software-center**

and then i searched the software center for pulseaudio and installed everything with that name and the sound started working.

Note: alot of ubuntu releases have a problem with the software-center not working (something to do with needing to add the policykit to startup)
To get it to work you either launch it from the terminal with gksudo

**gksudo software-center**

or run that command through alt+f2 (all graphical programs require gksudo)

[COLOR=Black][COLOR=Blue][COLOR=Black] 
[/COLOR] [/COLOR][/COLOR]

---

