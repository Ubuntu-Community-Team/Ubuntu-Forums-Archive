---
title: "Shell scripting support for a newbie :/"
date: 2006-06-04
forum: General Help
---

### Post by Kenzy on 2006-06-04
Hello!
This is my first post to this forum, so please tell me if I'm doing something wrong right now :P

And my stupid(?) question is:
I'm running Dapper Drake on my desktop and on my server. On my server I have an irssi-shell, and I would like to make a script for connecting to the server, and running "screen -r"- command after that. After an hour of googling I found some kind of tip for creating a little shell script, and it goes like this:
> 
$ vi irss1
#
# Irssi-script
#
clear
ssh serveri
screen -r

Where "serveri" is my server's hostname. I have made a keypair for ssh-connections from my desktop.
Obviously this script connects correctly to my server, but gives the "screen -r"- command to my desktop... so close <--> so far.

I would appreciate some clear solutions for my problem ](*,)

---

### Post by Ramses de Norre on 2006-06-04
That's because you're giving the screen command to the local shell and not to ssh. I don't think you can give ssh a command to execute when started.
Maybe (but I'm not sure that'll work) you could create a .bash_startup file in the home directory of the user on the server you're login into with ssh containing screen -r? I'm not sure about the layout of this file.

---

### Post by hegenious on 2006-06-04
I think one way to do it is give a user name before the command.

it would look something like this:

#
# Irssi-script
#
clear
ssh  -l <username> serveri screen -r

where <username> is the username logging in to serveri and subsequently will run the command screen -r


hope this helps  :p

---

### Post by xerosis on 2006-06-04
[QUOTE=hegenious]I think one way to do it is give a user name before the command.

it would look something like this:

#
# Irssi-script
#
clear
ssh  -l <username> serveri screen -r

where <username> is the username logging in to serveri and subsequently will run the command screen -r

hope this helps  :p[/QUOTE]

it should be username@serveri

---

### Post by Kenzy on 2006-06-04
Goddamn you guys are fast! Thanks for the quick reply. I tried this username-trick, the script does "work", but terminal gives me "Must be connected to a terminal."-message. Script clears the screen correctly, but doesn't establish ssh-connection. Any kind of an idea what does this error mean?

EDIT: and I also tried this ssh -l username@serveri screen -r, and this gives me the usage-help of ssh-command. When I removed the -l, I got the same "Must be connected to a terminal"- message.

---

### Post by hegenious on 2006-06-04
no, I think without the @
that's what the -l is for if you just want to run a remote command.

use the user@box login when you want to login and get a terminal opened on box

so it's either "-l username servername command" or "username@servername" but the last one opens a terminal on the remote host but I'm not sure if that is what you want.

---

### Post by Kenzy on 2006-06-04
Hmm. This really goes interesting. This screen -r-command doesn't seem to be working in a script like that, so I tried something else:
> 
#
# Irssi-script
#
clear
ssh -l janne serveri iwconfig

And typing ./irss1, I had correctly:
> 
lo        no wireless extensions.

sit0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"xxxxxxxxx"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:A0:C5:FF:EC:67
          Bit Rate:54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=69/100  Signal level=-65 dBm  Noise level:-194 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

There must be some trick for this :P

EDIT: It seems that this script only sends a remote command to the server, and gets the reply of that command to the desktop's terminal. The screen-r needs the remote-terminal to be opened... every other command works like a charm.

---

### Post by Kenzy on 2006-06-04
After all, I found somekind of a solution for my problem:

First, I made a keypair so I can connect to my server without password from now on. [Tutorial here](http://www.linuxproblem.org/art_9.html)
Then I made a script to my desktop's homedir
> 
echo "Launching irssi"
ssh username@serveri

And saved it to a filename "irs", where serveri is the hostname of my server.
After that I connected to my server via ssh, and edited my bashrc-file:
> 
pico .bashrc

and added a "screen -r"- line there.
After that just exit, and in terminal ~/./irs, and boom, my irssi opened.

Hope this helps someone as stupid as I am ;)

---

