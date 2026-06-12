---
title: "File type associations broken"
date: 2010-02-01
forum: General Help
---

### Post by Objekt on 2010-02-01
I am unable to double-click a file of a given type, e.g. .pdf, and have it open in the appropriate application.  While some file types have the correct associations, others do not, and I am unable to assign apps for some file types.

An example is Adobe portable document files ending in .pdf.  If I right-click on a .pdf in Nautilus, and select "Open with," I get a dialog containing two tabs.  One lists applications already associated with that file type, which at present is blank.  The other tab seems as if it should allow me to assign an application to that file type, but when I click it, the dialog simply closes suddenly, as if crashing.

What is going on here, and how do I fix it?

(Ubuntu 9.10 64-bit)

---

### Post by jimbob on 2010-02-01
Right click the file itself and select properties. Click the open with tab and click the radio button of the program you want to use as default.  If it is not there, add it with the selections down below.

---

### Post by akrostichon on 2010-02-05
Somehow I got the new absolute extension of the same problem.. :-( Not only my file type associations are broken but also my file types. 
 e.g. all bmp's are shown as executables, all jpg's are unknown, all odt's, xls,... are also unknown. 
  Basically: there are 2 file-types left: executable and unknown (while all files do have the correct filename extensions and can be opened with &quot;open with&quot; (which is then not saved because you can't associate unknown or executable file-types)) 
 
 thanks for any help

---

### Post by akrostichon on 2010-02-06
Well, I found some strange solution. I installed Xubuntu over Ubuntu and everything worked!

---

### Post by Objekt on 2010-02-08
> **jimbob said:**
> Right click the file itself and select properties. Click the open with tab and click the radio button of the program you want to use as default.  If it is not there, add it with the selections down below.

Doesn't work.  If I right click a .pdf for example, and select "Open With," the first two suggestions (Leafpad and gedit) are wrong.  If I choose instead "Open with another program," I get a dialog with two tabs.  One is "Recommended Applications" and is blank.  The other is "All Applications."  If I click "All Applications," instead of getting a list of apps or having the opportunity to choose one from /usr/bin, the entire dialog disappears abruptly.  I'd say that's a "crash."

Something about the file associations is deeply broken.

Is there some kind of central place where all the file types and info about which app should open them is stored?

---

### Post by Per Olav on 2010-02-08
I am also seeing this in 9.10, 64 bit. 

The previews are also broken, if you have ie a .jpg file, shouldn't there be a thumbnail image in the icon ?

---

### Post by Objekt on 2010-02-08
> **Per Olav said:**
> I am also seeing this in 9.10, 64 bit. 

The previews are also broken, if you have ie a .jpg file, shouldn't there be a thumbnail image in the icon ?

Right, I don't get those either (preview icons).  When I switch to Icon view, it's just a bunch of "generic file" icons (white rectangle with 1's and 0's on it).

oookay.. I just noticed something extremely weird.  Posting another thread about it now, since no one who knows how to fix things seems to be paying attention to this one.

New thread here: [http://ubuntuforums.org/showthread.php?t=1401605](http://ubuntuforums.org/showthread.php?t=1401605)

---

### Post by Per Olav on 2010-02-09
Thanks, but I don't see the point of posting several threads over the same issue. 
Anyway;
can any of you check if there is a bug filed for this? I can't access the site since my company is running a restrictive proxy.

---

### Post by Objekt on 2010-02-09
To hell with it.  Nautilus is just broken.  I believe it's time for an alternate file system browser.  Dolphin seemed to work fine when I was running Kubuntu 9.04, so I guess I'll try that.

---

### Post by Per Olav on 2010-02-10
Agreed. I'm going back to the 32 bit versjon, using PAE.

---

### Post by Objekt on 2010-02-24
Well, that's interesting!

I just noticed something very significant: When I open any of the following on the "Places" menu:

-Home Folder
-Desktop
-Bookmarks and subfolders (basically any subfolders in my /home folder)
-Removable Media and subfolders (mounted volumes that are not / or /home)

**I do NOT get Nautilus.**  Actually **pcman file manager is what's opening.**  Pcman does not have the ability to recognize file types or automagically know what app to open them with, I guess.

When I open the "Computer" item on "Places," Nautilus opens and all the file associations etc. work properly.

Uninstalled LXDE and pcman.  Wasn't using it anyway.

I think I know how Pcman got on my system.  A while ago, I installed Lightweight X Desktop Environment (LXDE), which carries with it Pcman as the file system browser.

Now the question is, how do I set things so that I always get Nautilus when opening any location in the Places menu?  I guess I could just uninstall LXDE, alternatively.

---

