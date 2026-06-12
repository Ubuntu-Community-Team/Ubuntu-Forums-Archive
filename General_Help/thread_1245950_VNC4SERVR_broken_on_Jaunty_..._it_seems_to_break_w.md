---
title: "VNC4SERVR broken on Jaunty ... it seems to break with each release of ubuntu"
date: 2009-08-21
forum: General Help
---

### Post by sefs on 2009-08-21
I am looking here...

[http://mondotech.blogspot.com/2008/04/grey-screen-with-vnc-server-gnome-kde.html](http://mondotech.blogspot.com/2008/04/grey-screen-with-vnc-server-gnome-kde.html)

and here...

[http://ubuntuforums.org/showthread.php?t=1078497&highlight=xstartup](http://ubuntuforums.org/showthread.php?t=1078497&highlight=xstartup)

and here...

[http://www.linuxquestions.org/questions/ubuntu-63/vnc4server-on-ubuntu-458240/](http://www.linuxquestions.org/questions/ubuntu-63/vnc4server-on-ubuntu-458240/)

I did not previously had a xstartup file in either /root/.vnc or ~/.vnc
so i created it in both places but I still am getting the grey screen.

H E L P!

Thanks.

---

### Post by sefs on 2009-08-21
Essentially xstartup was not needed by me.

All I needed to do was change "-query localhost" to -query 127.0.0.1" in the /etc/xinetd.d/Xvnc file, in the server_args part.

---

### Post by bbobbman on 2009-09-13
Installing vnc4server on Ubuntu 9.04  (Jaunty Jackalope)

-This article was based on [http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html](http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html). 

The routine below worked for me without any problems. 
    
Update the software (NEW) Installation
sudo apt-get update

Install the required applications: 
sudo apt-get install vnc4server xinetd xvnc4viewer

If you do not already have it installed, install ssh 
sudo apt-get install ssh

Open the “Login Window” applet in the System / Administration menu (you should be prompted for your password to access this).
-Choose the "Remote” tab and select one of the options from the Style dropdown. Select “Local”. 
-At the bottom of the tab, there is a button called "Configure XDMCP". Click and make sure that the "Honor indirect requests" is NOT selected.

Using your favourite text editor, open /etc/gdm/gdm.conf for editing. You will need superuser privileges 
sudo vi /etc/gdm/gdm.conf   (or nano etc...)

Note: The preferred file to edit is gdm.conf-custom as changes made to this file will survive an upgrade of GDM. 

Regarding the changes below, you should only need to add the RemoteGreeter line under [daemon] and AllowRemoteRoot under [security]. 

In the [daemon] section, uncomment (i.e. remove the leading '#' sign) from the line which starts "RemoteGreeter=/usr/lib/gdm/gdmlogin". 
In the [security] section, change the AllowRemoteRoot to false. 
In the [xdmcp] section, make sure Enable=true and HonorIndirect=false.

Next:
Create an entry for xinetd to start each time it receives a connect request, create a file called Xvnc in /etc/xinetd.d. 

In /etc/xinetd.d/Xvnc, put the following text: 

service Xvnc
{
type = UNLISTED
disable = no
socket_type = stream
protocol = tcp
wait = yes
user = root
server = /usr/bin/Xvnc
server_args = -inetd :1 -query 127.0.0.1 -geometry 1024x768 -depth 24 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vnc/passwd -extension XFIXES
port = 5901
}

Note: Important: The text starting at "server_args..." and ending at ".../root/.vncpassword" is all ONE line. (Copy and paste may put text on a new line)
Note: Add "-extension XFIXES" to the end of the "server_args" line to get past the End of Stream problem.

Create an entry in the /etc/services file (at the bottom of the file)
Xvnc            5901/tcp        #Xvnc

Create a password for xinetd, by running:
sudo mkdir /root/.vnc 
sudo vncpasswd /root/.vnc/passwd

Note: xstartup was not needed in my install.

Restart xinetd by running: 
sudo /etc/init.d/xinetd stop
sudo killall Xvnc
sudo /etc/init.d/xinetd start

You may also need to reboot to get some of the other changes to take effect.

To test that it is working:
xvnc4viewer :1

To start a session on the machine, 

or

Connect from another machine using a client like RealVNC. 

You should get a graphical login (not a grey screen).

NOTE: The session created does not end if you terminate the connection. It persists until you actually log out. This is useful if you are on a connection that drops out or if you login to start a job and need to disconnect without killing the job.

Patrick

---

