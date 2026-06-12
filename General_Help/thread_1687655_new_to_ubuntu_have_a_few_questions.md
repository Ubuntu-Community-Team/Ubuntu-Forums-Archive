---
title: "new to ubuntu have a few questions"
date: 2011-02-14
forum: General Help
---

### Post by speckmc on 2011-02-14
im extremely new to this, so excuse my child like wonder and amazement..... im a windows server admin with 10 years experience in the windows server world... so you can imagine my handycap when coming over to the Linux side....

command line isn't a problem for me as i have been working on cisco devices for awhile as well..  just trying to learn all these new commands!

its a pretty simple thing i am setting up for a starter, just a web server, with an ftp server on it.. at least that's the theory behind what id like to do.......

so Ive done all of that.. installed vsftpd, and im running into an issue when i try to edit vsftpd.conf  says permission denied.. :-s  so as such, my thoughts are... "well you moron what did you do wrong!"

id like to get linux down good, because i may take the IT side of things more in a linux direction here! 

so heres what i did... i burned an ubuntu 10.10 server disk, and installed it on a poweredge 1750 i had lying about, installed lamp server, that works 

then i installed vsftpd

id like to edit it, so that i can allow uploads, and allow users to log into it (1 or 2) to upload things to the web server... 

unsure if i NEED to, but would it be wise to install something like kubuntu desktop so that i can bring up that to edit things? seeing as i am coming from windows server world....? 

on a random side note, i will tell you, i absolutely love ubuntu, we run server 2k3 and term svcs here, and id highly consider changing the whole place over to linux if the users would be able to figure it out haha

so anyways what are a few pointers you can give a windows person switching over? lol

---

### Post by mastablasta on 2011-02-14
Here is a good free linux command e-book: 
[http://linuxcommand.org/](http://linuxcommand.org/)
 
Though it's based for red hat i believe most commands are the same.
 
you do not need a desktop installed to run the server, but you can install it if you wish.
 
have you tried with sudo command?

---

### Post by oldfred on 2011-02-14
Ubuntu is different that other Linux distributions in that it uses sudo for temporary administrative rights rather than having you log in as the administrator and forgetting to log back in as a user.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

I still find I forget sudo, so whenever a command does not work, I just go back and add sudo. But this one have never ever worked for me:
[http://xkcd.com/149/](http://xkcd.com/149/)

---

### Post by speckmc on 2011-02-14
> **mastablasta said:**
> Here is a good free linux command e-book: 
[http://linuxcommand.org/](http://linuxcommand.org/)
 
Though it's based for red hat i believe most commands are the same.
 
you do not need a desktop installed to run the server, but you can install it if you wish.
 
have you tried with sudo command?


ill have to check this out, ill try again with the sudo command..;)

---

### Post by cyb3r_sn4k3 on 2011-02-14
Sudo should work it was one of first habits which I found a little hard to imply at first when I migrated from Windows to Linux. :D And the different type of file system was a problem for me for a few days too.

---

### Post by deserthowler on 2011-02-14
You might want to add a window manager like TWM to use a few graphics programs like gedit or firefox.  Won't take as much resources as a full blown KDE or Gnome install.

Earl

---

### Post by speckmc on 2011-02-14
resources aren't too big of a deal to me, its not going to be a site that has that much traffic, and the machine does have 2 3.2ghz dual cores, and 4gb of mem

ok, so when i do /etc/vsftpd.conf    it says permission denied....

so i try sudo /etc/vsftpd.conf    ..   command not found.. so i feel like a retard!! hahaha):P   i know im doing something wrong  im going to read that link now!

if anyone has any suggestions or wants to point and laugh feel free!!

god i feel like such a newb! i haven't felt like this in a long time!

---

### Post by coldraven on 2011-02-14
I've not played with the server edition, yet, but here's a handy command
```
man -k editor
```
which will list the man (manual) pages of all the editors installed.
Obviously it can do the same for other utilities other than an editor.
I found this quite useful if I did not know the name of a command. Now I have reams of post-it notes with them on :)
I actually use tomboy notes.
Have fun!

---

### Post by speckmc on 2011-02-14
> **coldraven said:**
> I've not played with the server edition, yet, but here's a handy command
```
man -k editor
```which will list the man (manual) pages of all the editors installed.
Obviously it can do the same for other utilities other than an editor.
I found this quite useful if I did not know the name of a command. Now I have reams of post-it notes with them on :)
I actually use tomboy notes.
Have fun!


i think im going to have to invest in a notebook to write down commands in.. haha..

---

### Post by oldfred on 2011-02-14
sudo nano /etc/vsftpd.conf

Or your favorite editor.

If you install a window manager.

gksudo gedit /etc/vsftpd.conf

gksudo for graphical applications.

---

### Post by Chris Musampa on 2011-02-14
> **speckmc said:**
> resources aren't too big of a deal to me, its not going to be a site that has that much traffic, and the machine does have 2 3.2ghz dual cores, and 4gb of mem

ok, so when i do /etc/vsftpd.conf    it says permission denied....

so i try sudo /etc/vsftpd.conf    ..   command not found.. so i feel like a retard!! hahaha):P   i know im doing something wrong  im going to read that link now!

if anyone has any suggestions or wants to point and laugh feel free!!

god i feel like such a newb! i haven't felt like this in a long time!

You're trying to get it to execute the config file as you haven't specified an editor:

sudo nano /etc/vsftpd.conf


should do the trick (if you don't insert 'sudo' nano would still allow you to edit the file but you wouldn't be able to save it to the same location)

---

### Post by speckmc on 2011-02-14
> **oldfred said:**
> sudo nano /etc/vsftpd.conf

Or your favorite editor.

If you install a window manager.

gksudo gedit /etc/vsftpd.conf

gksudo for graphical applications.



thank you!  i got lazy and just went ahead and installed ubuntu desktop LOL

im still fiddling command line through that, however it makes it easier to associate i guess when i have a gui..  old habits die hard?

i appreciate the help!, now that ive gotten my ftp side configured its time to get a website going on this thing!

---

### Post by speckmc on 2011-02-14
> **Chris Musampa said:**
> You're trying to get it to execute the config file as you haven't specified an editor:

sudo nano /etc/vsftpd.conf


should do the trick (if you don't insert 'sudo' nano would still allow you to edit the file but you wouldn't be able to save it to the same location)


see i knew i was doing something retarded!!  haha ill figure this out yet!  im using gedit now, so i likes it

hell i may set all my own stuff up under linux, as im starting my own side business, and man im really loving linux so far

---

### Post by Topsiho on 2011-02-14
It's great to see a windows server admin with 10 years experience have the guts to explore a new world. I wish there were more of those like you :p

I am not an admin at all, but feel obliged to tell you that servers usually are installed without a GUI, and with a bare minimum of software, only that which is really necessary.

On almost any Linux box however one edits files using vi or the improved version, vim. If not present in your current install, you'l find it in the repositories.

Learning vim is not really easy, though I can use it with only a very few commands in my repertoire. An admin should put some more energy to it, however. The bonus is that you can administer almost any Linux box using vim.

Good luck to you :)

Topsiho

---

### Post by wormyblackburny on 2011-02-14
+1 to Topsiho's comment. Get familiar with VI editor as it is used in the majority of Unix flavors, and as he said most server platforms lack a gui interface. Here is a handy cheatsheet for using VI: [http://www2.cs.uidaho.edu/~rinker/ed03.pdf]("http://www2.cs.uidaho.edu/%7Erinker/ed03.pdf")

---

### Post by mastablasta on 2011-02-15
thanks for the cheatsheet. might come in handy.
 
btw this VI really reminds me of edlin or what was that old DOS editor in 80's. is there nothing a little bit more graphical (at least VGA graphics) like edit was in last DOS versions?

---

### Post by speckmc on 2011-02-15
sounds good, yea i may kill this one and redo everything without the gui, i dont care about a gui so much, unless im working on my work station hah!.. i grew up playing around in dos, so command line isnt a big deal, gui is just the lazy mans way of doing things i guess... i just got frustrated with it and tossed the gui on there..

i find im still having to do most things from the terminal window anyways.. so it feels like im in windows again.. sitting there with a wasted gui staring me in the face will i do things in command prompt ! atleast its not booring to look at i guess? hahaha

i appreciate all the advice, and replys..  

yes this is definetly something new for me... never touching linux in my life to "hey lets throw a linux web server into production itll be great!" i may actually look at going and taking a class to get better involved in linux, and look at maybe a linux+ cert..  who knows!   starting to wish i had built my pbxnsip server on linux now! i mean granted it works fantastically on server 2k3... it may just have been that touch more stable on a linux box.. but i have a feeling id be getting into some huge things with that.. as i have redundant fiber connections going into that thing.... lol

i actually had to do some funny things on it to get some aspects of it to work, mainly the on-hold music. as the machine has no sound hardware. and if i load the on-hold mp3 into the software it simply starts it anew whenever a person is put on hold, which wouldnt work for our on-hold recording!

needless to say virtual audio cable, winamp, and change a few settings and my on-hold is now looping its way along happily.. lol 

thats another story though... !

again than you for all the help and responses...  and sorry if my reply is scatter-brained... unfortunately i am in such a situation today where im playing fireman again... too many problems, not enough me.. lol

---

### Post by speckmc on 2011-02-15
i do have another question....  im looking it up as i type this but wanted to have opinions on it..

in all my windows boxes, i have 2+ nic's running in a load balancing fail over team

id like to do something like this on the linux box, what would be involved?

---

### Post by debd on 2011-02-15
I guess you tried to edit a file that belongs to the sys root.

try this:
press Alt+F2
type in:   gksudo nautilus
enter ur password

now go to the file you want to edit & get it done!

---

### Post by oldos2er on 2011-02-15
[https://help.ubuntu.com/10.04/serverguide/C/security.html](https://help.ubuntu.com/10.04/serverguide/C/security.html)

---

### Post by Topsiho on 2011-02-16
I googled with nics load balancing ubuntu and found: 

[http://blog.brightbox.co.uk/posts/howto-do-ethernet-bonding-on-ubuntu-properly](http://blog.brightbox.co.uk/posts/howto-do-ethernet-bonding-on-ubuntu-properly)

It says the networking in Ubuntu is a bit opaque, however, and that HowTo's get obsolete fast. Still it might be of some help.

You might also google for Linux generally :)

Greets,

Topsiho

---

### Post by speckmc on 2011-02-16
ok im confused now..... everything was visbile on the net before i installed ubuntu desktop....

now that ive done that, nobody can hit the bloody web server from the outside world.. i can hit it on my network all day long.. but not from the outside...


no firewall, port 80 is open..  this makes no sense..!

---

### Post by Vaphell on 2011-02-16
check if the network manager applet didn't take over, you know that thing on gnome panel. My box is inaccessible unless someone logs in so the applet can run and initialize network stuff.

---

### Post by speckmc on 2011-02-16
> **Vaphell said:**
> check if the network manager applet didn't take over, you know that thing on gnome panel. My box is inaccessible unless someone logs in so the applet can run and initialize network stuff.


ho do i do that, and how would i kill it? lol

seriously it all stopped working right after i installed gnome....  fantastic eh

---

### Post by Vaphell on 2011-02-16
so is that the problem? have you checked if the computer in fact becomes visible to the outside world when you log in to gnome and dissapears when you log out?

what is in your /etc/network/interfaces ?
afaik some people hardcode the configuration there and uninstall network-manager(-gnome) stuff entirely.

---

### Post by speckmc on 2011-02-17
> **Vaphell said:**
> so is that the problem? have you checked if the computer in fact becomes visible to the outside world when you log in to gnome and dissapears when you log out?

what is in your /etc/network/interfaces ?
afaik some people hardcode the configuration there and uninstall network-manager(-gnome) stuff entirely.


ill make that attempt now and ill check that config file....

if i dont get something functioning today im going to kill the whole server and do this again without a gui, im capable of doing it all without it, was just being lazy lol

---

### Post by speckmc on 2011-02-17
ok so get this.. i did what you said.. i went in and hardcoded what i wanted in /etc/network/interfaces

and sudo apt-get remove network-manager network-manager-gnome

rebooted, and BAM traffic coming in again.....

beautifull  id like to kill the whole damn gui, but im worried it might play hell on everything now..

---

