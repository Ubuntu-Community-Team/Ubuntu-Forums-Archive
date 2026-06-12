---
title: "GIMP 2.6.7 Won't Load in Ubuntu 9.1 Karmic Koala"
date: 2010-01-26
forum: General Help
---

### Post by Gotou on 2010-01-26
Hello!

When I click on the Applications -> Graphics -> GIMP Image Editor icon GIMP doesn't load.  Instead a task bar button appears in the lower task bar for a brief moment and then disappears.  I've tried starting GIMP through the terminal with "gimp-2.6" and all that comes back is "Segmentation fault".

I came across a recent thread here on the forums where a GIMP/Photshop adaptation was the culprit.  I just have the regular GIMP installed.

I've removed GIMP through Synaptic, rebooted, reinstalled GIMP through Synaptic, rebooted and still GIMP won't load and I still get the same response in the terminal.

It is possible that I've managed to mess up my system in such a way that GIMP will never run unless I wipe out Ubuntu completely and reinstall everything again.  However, I don't use GIMP enough to warrant dumping everything and starting over.

Is anyone else experiencing this problem?  If so, is there a fix or a patch in the works?

Thanks!

---

### Post by fragos on 2010-01-26
Just a guess but perhaps your problem is in a configuration file. Open your Home folder in Nautilus and do a Ctrl-H to show hidden files. Search for .gimp-2.6 and delete that folder. When a package is removed it leaves it's operating configuration files in your Home folder. Installing the package again won't overwrite these files if they exist, only create them if they don't exist.

---

### Post by symon1980 on 2010-01-26
try to  open gimp in a terminal and paste the output to me

applications, accessories, terminal. just type in      gimp

---

### Post by Gotou on 2010-01-28
Thanks for the suggestions.

@Fragos:
As suggested I looked through Nautilus with the hidden files shown but did not find a ".gimp-2.6" folder nor a file.  I performed a search through my home folder and all subfolders with the option to show hidden or system files and still no ".gimp-2.6" folder/file.

@symon1980:
In the terminal I typed in "gimp" (without quotes) and the output was "Segmentation fault".  I get the same output when I enter "gimp-2.6".

I just ran Synaptic to see if any updates would tickle the GIMP into working but still no luck yet.

Any other ideas?

---

### Post by fragos on 2010-01-28
Did you find a folder ".gimp". My system may be a little different since I install Gimp update that don't come from Ubuntu.

---

### Post by Gotou on 2010-01-30
@Fragos:
I performed a search through the "File System" ( / ) for ".gimp" with the option to show hidden and backup files.  The results came up with nothing.

Then I performed the search again for "gimp".  "1,277 Files Found".  The results were any file name that contained "gimp".  Only one file was in my home directory and when I opened it in Gedit the file appears to be for the "Applications" menu list (gimp.desktop ~$ ./local/share/applications).  The other files were mostly located in subfolders of /usr.]

This one is a head scratcher.:-k

---

### Post by fragos on 2010-01-30
> **Gotou said:**
> @Fragos:
I performed a search through the "File System" ( / ) for ".gimp" with the option to show hidden and backup files.  The results came up with nothing.

Then I performed the search again for "gimp".  "1,277 Files Found".  The results were any file name that contained "gimp".  Only one file was in my home directory and when I opened it in Gedit the file appears to be for the "Applications" menu list (gimp.desktop ~$ ./local/share/applications).  The other files were mostly located in subfolders of /usr.]

This one is a head scratcher.:-k

I checked my ./local/share/applications and although I use Gimp there was no gimp.desktop there. I'm not sure of the purpose of this folder since it's use appears inconsistent. ".desktop" files are launchers. When on the desktop you could click them to start an ap without a specific file just like in the Application Menu. When you click a file it's mime type will determine which aps can execute that file. That launch information comes from the Applications Menu.

Gimp may store it's configuration data in a non-Gnome way. My last suggestion is to uninstall Gimp and then delete all remaining files and folders you "locate" with gimp in the file name.

---

### Post by rickc1970 on 2010-01-31
I'm having a similar problem. I tried it and after it wouldn't work I uninstalled it and looked for a gimp folder in my home directory. There were no folders there for gimp. There was one in the file system but it wouldn't let me delete that folder. 

I reinstalled it and it still wouldn''t work. So I tried it in Terminal and got the following message: 
 rick@rick-laptop:~$ gimp
/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory

(gimp:3748): LibGimpBase-WARNING **: gimp: wire_read(): error

Gimp did owrk through terminal even with that message although whe I closed the terminal window it closed gimp. Any idea how to fix this? Also I did a system update today. Before the update Gimp did work normally.

---

### Post by Gotou on 2010-02-07
Just to give an update, I was feeling masochistic and decided to wipe out Ubuntu and reinstall.  GIMP is working now but it's taken me several days to get things reconfigured back to the way I need them to be.  Uggg...](*,)

Till the next time I manage to mess things up, thanks to all!

---

### Post by GoodPeace on 2010-02-24
I had a similar problem, and tried to re-install gimp and found that the xsane scanner depended on libgimp v2.6.8, while my synaptic were trying to install a gimp v2.6.7.

Then I remembered, that after my upgrade to karmic, most of my custom repositories had been disabled by the upgrade tool. After enabling them, and updating the package list, I simply used apt-get to install gimp, and it all works now.

---

