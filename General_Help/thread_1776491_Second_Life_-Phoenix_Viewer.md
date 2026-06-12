---
title: "Second Life -Phoenix Viewer"
date: 2011-06-06
forum: General Help
---

### Post by sanjeevpunj on 2011-06-06
I play Second Life and I use the Phoenix Viewer. The Linux download is available at [http://www.phoenixviewer.com/downloads.php](http://www.phoenixviewer.com/downloads.php) and the file that I downloaded to my Downloads Folder is called 
**PhoenixViewer-i686-1.5.2.1102.tar.bz2 **
and I don't know how to proceed further.Any suggestions welcome, I want to get back to my game, or I have to return to Windows XP to play. Thank You.

---

### Post by pqwoerituytrueiwoq on 2011-06-06
depends on what is in it it may need compiling or may have the executable inside
it appears to be menu for use on 32 bit systems based on the file name

---

### Post by pqwoerituytrueiwoq on 2011-06-06
now that i downloaded it
it has a file called [FONT=Courier New]README-linux.txt[/FONT] in it read it will tell you want to do

---

### Post by sanjeevpunj on 2011-06-06
> **pqwoerituytrueiwoq said:**
> now that i downloaded it
it has a file called [FONT=Courier New]README-linux.txt[/FONT] in it read it will tell you want to do

Thanks I will read it up!

---

### Post by sanjeevpunj on 2011-06-06
Well I read the document.There is some instruction to run ./secondlife from the directory where this file is downloaded.I just cannot figure how to proceed here! I tried running in terminal the following command

tar -jxvf PhoenixViewer-i686-1.5.2.1102.tar.bz2 

and here are the results:
I could not copy the entire stuff, but from somwhere upto the end here it is.

PhoenixViewer-i686-1.5.2.1102/skins/default/xui/en-us/menu_login.xml
PhoenixViewer-i686-1.5.2.1102/skins/default/xui/en-us/menu_viewer.xml
PhoenixViewer-i686-1.5.2.1102/skins/default/xui/en-us/floater_html.xml
PhoenixViewer-i686-1.5.2.1102/skins/default/xui/en-us/floater_animation_preview.xml
PhoenixViewer-i686-1.5.2.1102/skins/default/xui/en-us/floater_group_info.xml
PhoenixViewer-i686-1.5.2.1102/skins/default/xui/en-us/mime_types_mac.xml
PhoenixViewer-i686-1.5.2.1102/skins/default/xui/en-us/floater_media_browser.xml
PhoenixViewer-i686-1.5.2.1102/skins/default/xui/en-us/floater_moveview.xml
PhoenixViewer-i686-1.5.2.1102/skins/default/xui/en-us/floater_region_info.xml
PhoenixViewer-i686-1.5.2.1102/skins/default/xui/en-us/strings.xml
PhoenixViewer-i686-1.5.2.1102/skins/default/xui/en-us/floater_report_abuse.xml
PhoenixViewer-i686-1.5.2.1102/skins/default/xui/en-us/floater_object_im_info.xml
PhoenixViewer-i686-1.5.2.1102/skins/default/colors.xml
PhoenixViewer-i686-1.5.2.1102/snowglobe
PhoenixViewer-i686-1.5.2.1102/licenses.txt
PhoenixViewer-i686-1.5.2.1102/gpu_table.txt
PhoenixViewer-i686-1.5.2.1102/gridargs.dat

Now I have no inkling, how to proceed.

---

### Post by pqwoerituytrueiwoq on 2011-06-06
just proceed to the next step it was just telling you what was in it
when/if it starts giving errors then there is a issue

tar -jxvf PhoenixViewer-i686-1.5.2.1102.tar.bz2
is the same thing as right clicking it and pressing extract

---

### Post by sanjeevpunj on 2011-06-06
The entire set of Instructions are here-

The Second Life Linux client entirely runs out of the directory you have
unpacked it into - no installation step is required.

Run ./secondlife from the installation directory to start Second Life.

For in-world MOVIE and MUSIC PLAYBACK, you will need (32-bit) GStreamer 0.10
installed on your system.  This is optional - it is not required for general
client functionality.  If you have GStreamer 0.10 installed, the selection of
in-world movies you can successfully play will depend on the GStreamer
plugins you have; if you cannot play a certain in-world movie then you are
probably missing the appropriate GStreamer plugin on your system - you may
be able to install it (see TROUBLESHOOTING).

User data is stored in the hidden directory ~/.secondlife by default; you may
override this location with the SECONDLIFE_USER_DIR environment variable if
you wish.

---

### Post by pqwoerituytrueiwoq on 2011-06-06
it may be necessary to make [FONT=Courier New]./secondlife[/FONT] executable
[FONT="Courier New"]chmod +x ./secondlife[/FONT]

---

### Post by sanjeevpunj on 2011-06-16
Thanks man, I wrote to Phoneix Support, and they asked me to create an executable launcher using the "snowglobe" file in the Phoenix folder.Eventually runs, though some streaming sound issues are still to be ironed out.Thanks so much for the time you guys took to reply.Cheers.

---

### Post by keithunder on 2011-07-05
This is completely confusing!

Run ./secondlife from the installation directory to start Second Life.

what does that mean?

Does it mean go to the terminal and run stuff like in dos,

I tried that and it says Run: command not found

then without the run
bash: ./secondlife: No such file or directory


keith@keith-GA-MA770T-UD3P:~/SL$ chmod +x ./secondlife
chmod: cannot access `./secondlife': No such file or directory


Is there not a way of installing pheonix through the Ubuntu software centre?

---

### Post by SatanSpawn on 2011-09-12
The command to start Phoenix is <code>./snowglobe</code>

Btw is the streaming issue a build issue, or software incompatibility, cause if anyone has had luck building from source... i would like to know!

---

