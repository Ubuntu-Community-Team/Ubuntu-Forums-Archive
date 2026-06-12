---
title: "anybody get Lotus Notes 8.5.1 (any FP) on 10.04 lucid 32bit to work?"
date: 2010-05-02
forum: General Help
---

### Post by wgstelz on 2010-05-02
I have been researching and fighting with trying to get lotus notes 8.5.1 installed on lucid. I found posts on people getting it to work on the 64 bit version of lucid, but nothing on 32bit.  I have also logged a case with IBM to try and get this fixed.

When I try to install the deb I get dependency errors: libgnome-desktop-2, libgnome-desktop-2-7, and libgnome-desktop-2-11

I was hoping the newer versions of these apps would work with notes, so I tried a dpkg -i --force-all, which installed the program, but it was mostly unusable, plus I kept getting an error when trying to install something else with aptitude (asking me to run sudo apt-get -f install) which wanted to remove the notes install.  

Any help will be much appreciated!!

Walt
:confused::confused:

---

### Post by virtual50 on 2010-05-03
Hi, same problem with Ubuntu 10.04 LTS 32bits.  It was working very well in Ubuntu 9.10 32bits

---

### Post by dino99 on 2010-05-03
have you tried with wine (winehq) and lotus for windoz ?

---

### Post by omniphil on 2010-05-03
I'm in the same boat too. I have heard Notes 8.5.2 Beta works in 10.04 but I am unable to find it as of yet.

Currently as a work around i'm using vmware player 3.0.1 and running it in unity mode. Which actually runs notes 8.5.1 better than 8.5.1 used to run under ubuntu 9.10.

Still would like to run it native tho, so hopefully someone will figure this one out...

---

### Post by vtzhang on 2010-05-04
I got Lotus Notes 8.5.1 working on 32-bit Lucid Lynx.

1. Manually install libgnome-desktop2. I used a hardy deb at:  [http://packages.ubuntu.com/hardy/i386/libgnome-desktop-2/download](http://packages.ubuntu.com/hardy/i386/libgnome-desktop-2/download). Lucid  already has libgnome-desktop-2-17 installed, so this just solves the  dependency issue
2. Run sudo apt-get install libgnomeprintui2.2-0 ttf-xfree86-nonfree
3. Install the Lotus Notes fixpack (optional?)
4. Follow step 4 of  [http://usablesoftware.wordpress.com/2010/03/09/installing-lotus-notes-8-5-1-fp1-on-ubuntu-10-04-lucid-lynx-64bit/](http://usablesoftware.wordpress.com/2010/03/09/installing-lotus-notes-8-5-1-fp1-on-ubuntu-10-04-lucid-lynx-64bit/),  but sudo apt-get install the libraries instead of using getlibs, since  it's unnecessary for 32-bit
5. Follow step 5 of the same site

Sametime is also working for me.

---

### Post by vtzhang on 2010-05-04
For the apt-get install error, just sudo apt-get remove (everything that is causing the problem, including ibm-lotus-notes).

---

### Post by wgstelz on 2010-05-06
Let me add one more:  [http://gordonazmo.wordpress.com/2010/04/07/lotus-notes-8-5-a-gdk-window-is-being-destroyed-out-of-destroywindow-ubuntu-10-4/](http://gordonazmo.wordpress.com/2010/04/07/lotus-notes-8-5-a-gdk-window-is-being-destroyed-out-of-destroywindow-ubuntu-10-4/)

After following jtzhang's first post and the link above all appears to be well. ( 5 minutes of playing so far)

Thanks

Walt

---

### Post by omniphil on 2010-05-06
Mine is now working as well.

All I needed to do was manually install the libgnome-desktop2 as listed above, from there I installed the 8.5.1 package followed by the fixpack.

This gets the client working somewhat.

From there I installed the fonts and the 4 libraries from the above post.

That's all I needed. The only thing different really from 9.10 was the first step to get the libgnome-desktop2 installed, everything else was the same as 9.10...

---

### Post by w2no on 2010-05-08
hello friend.  can u detail the process pls?
i m on the Ubuntu 10.04 which i installed into the Windows 7.
may u help me up? do wish to learn and get Lotus Notes working on Ubuntu :)
thanks before hand,

---

### Post by echofloripa on 2010-05-10
"I found posts on people getting it to work on the **64 bit version of lucid**, but nothing on 32bit"

Where? I've searched everywhere and couldnt find it.

---

### Post by omniphil on 2010-05-10
> **w2no said:**
> hello friend.  can u detail the process pls?
i m on the Ubuntu 10.04 which i installed into the Windows 7.
may u help me up? do wish to learn and get Lotus Notes working on Ubuntu :)
thanks before hand,


Here's my steps on 32bit...

1. [http://packages.ubuntu.com/hardy/i386/libgnome-desktop-2/download](http://packages.ubuntu.com/hardy/i386/libgnome-desktop-2/download)    download and install that package.

2. sudo apt-get install libgnomeprintui2.2-0

3. sudo apt-get install ttf-xfree86-nonfree

4. install Notes from the .deb file

5. Go here and get the four files shown   [http://www.freetechie.com/upload/lotus_notes/](http://www.freetechie.com/upload/lotus_notes/)

6. Move those 4 files to the /opt/ibm/lotus/notes  But you wont have access to that folder so...   sudo mv lib* /opt/ibm/lotus/notes


That should do it....

---

### Post by w2no on 2010-05-13
> **omniphil said:**
> Here's my steps on 32bit...

1. [http://packages.ubuntu.com/hardy/i386/libgnome-desktop-2/download](http://packages.ubuntu.com/hardy/i386/libgnome-desktop-2/download)    download and install that package.

2. sudo apt-get install libgnomeprintui2.2-0

3. sudo apt-get install ttf-xfree86-nonfree

4. install Notes from the .deb file

5. Go here and get the four files shown   [http://www.freetechie.com/upload/lotus_notes/](http://www.freetechie.com/upload/lotus_notes/)

6. Move those 4 files to the /opt/ibm/lotus/notes  But you wont have access to that folder so...   sudo mv lib* /opt/ibm/lotus/notes


That should do it....

Omni, in step 4, where can i get the .deb?  pls kindly advise.

---

### Post by omniphil on 2010-05-13
> **w2no said:**
> Omni, in step 4, where can i get the .deb?  pls kindly advise.

Lotus Notes is not a free program, so if you are using it at work you'll need to downloaded from IBM through your IBM download page...

---

### Post by w2no on 2010-05-16
oic... i ll need to contact my IT for help  then :)

---

### Post by larsberntrop on 2010-05-18
> **omniphil said:**
> Lotus Notes is not a free program, so if you are using it at work you'll need to downloaded from IBM through your IBM download page...

Actually Lotus Notes IS free for personal use! You can confirm this by going to: [http://www.ibm.com/developerworks/downloads/ls/dominodesigner/learn.html]("http://www.ibm.com/developerworks/downloads/ls/dominodesigner/learn.html")

---

### Post by cooktony on 2010-06-01
Does anybody have another link for the 4 files in step 5? It appears to be down.
Thanks

---

### Post by ugutugut on 2010-06-02
The 4 files are:
  libgdk_pixbuf-2.0.so.0 
  libgdk_pixbuf_xlib-2.0.so.0 
  libgdk-x11-2.0.so.0 
  libgtk-x11-2.0.so.0 

[http://rapidshare.com/files/394640532/libgtk.zip.htm](http://rapidshare.com/files/394640532/libgtk.zip.htm)

---

### Post by jongudm on 2010-08-09
Related to the OP, do any of you know if Lotus Notes 8.5.1 will keep working properly through an upgrade from 9.10 to 10.04 when done with Update Manager?

---

### Post by virtual50 on 2011-11-02
Hi, just for update: 8.5.2 works well with Lucid 10.04

---

