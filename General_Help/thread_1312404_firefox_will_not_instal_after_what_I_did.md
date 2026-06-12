---
title: "firefox will not instal after what I did"
date: 2009-11-03
forum: General Help
---

### Post by deankovell on 2009-11-03
I uninstalled firefox and then deleted everything that came up on a file search for "firefox" and just to be sure I got it all, I deleted everything that came up on a search for "mozilla". seemed like a good idea at the time; now however,  Firefox installs, but  the launcher's not turning up in the application menu.  I've been trying since yesterday to undo what I've done, would somebody please help me out.  Thanks in advance.
This is firefox 3.5 in Karmic

---

### Post by dbyjazz on 2009-11-03
see what happens when you run "firefox" in terminal.

---

### Post by deankovell on 2009-11-03
thanks for the fast reply 

I get 
```
The program 'firefox' can be found in the following packages:
 * firefox-3.5
 * firefox-3.0
Try: sudo apt-get install <selected package>
firefox: command not found

```
apt-get install just tells me that it's already installed

I also just used synaptic for something else and this was part of the details during that installation.
```
Dpkg: warning: files list files for package 'firefox-3.5' missing, assuming package has no files currently installed.
```
and repeated the mesage, but for 'firefox-3.5-branding'

---

### Post by scouser73 on 2009-11-03
Ok, firstly it seems that you've totally messed up installing Firefox.  Let me try and help you sort it out.

**1** - Right click & Extract the Firefox tar.bz2

**2** - Enter **gksudo nautilus** in Terminal

**3** - Copy & paste the Firefox file that you have just extracted to **/opt**

**4** - Right click on the Ubuntu start logo, select **Edit Menus**, 

**5** - Highlight the Internet sub menu & click New Item

**You will now see a small dialogue box appear**

**6** - In the Name field, type **Firefox**

**7** - In the Command field type **/opt/firefox/firefox**

**8** - In the Comment field type **Firefox**

You will now have Firefox installed.

---

### Post by deankovell on 2009-11-03
you're awesome scouser73.
   It works! Hwoever, I checked, and that message for the "files list files..." still comes up in synaptic. Is this going to have implications for running updates? 
The updates thing is not that immediate of an issue for me, I'm just glad I got firefox back, even though seamonkey's starting to grow on me.
Thanks guys

---

### Post by joelandsonja on 2009-11-03
I realize this is an old post, but scouser73 deserves a medal for this one!

---

### Post by wildweathel on 2009-11-03
"It seemed like a good idea at the time"

Oh, boy.  No, it wasn't.  For future reference, if you want to remove a program, "sudo apt-get remove *whatever*" is the way to go.  Or, use System -> Administration -> Synaptic.

To fix that error message, I'm pretty sure this will work:
```

sudo apt-get update
sudo apt-get remove firefox-3.5 firefox-3.5-branding

```

Cause: dpkg keeps a list of files installed by the firefox-3.5 and firefox-3.5-branding packages.  You removed these lists, since they have firefox in their names, so now dpkg is confused.

You'll still have the firefox install from following scoser's instructions, so you can leave it at that.  

Note that other programs may be broken, if they installed a file with firefox or mozilla in the name.  If you have trouble with other things breaking down the road, please mention this.

---

### Post by deankovell on 2009-11-03
> scouser73 deserves a medal for this one! 
absolutely
 **wildweathel** too

---

