---
title: "Tutorial: Play PSX games on Linux (ePSXe)"
date: 2010-07-09
forum: General Help
---

### Post by d3v1150m471c on 2010-07-09
If you're interested in playing your psx games on linux this is the tutorial for you. If you've tried your luck with pcsx and ePSXe_1_6_0 ( linux version of ePSXe ) and failed miserably like myself, you've clicked the right link. For this tutorial we'll be using ePSXe and wine1.0 or wine1.2.

1. Install wine if you haven't already. I've had success with both versions but currently use 1.2. You may have better results with that version.

```

sudo apt-get install wine
# yum install or a variation for non-ubuntu distros

```2.  Download ePSXe, zlib1.dll, a GPU plugin, and scph1001.bin . Please note, to use scph1001.bin or another playstation bios binary you must first legally own one to also own a backup copy. There is a modified copy of the ePSXe170 that already contains two GPU plugins and several bios binaries with the zlib1.dll file. This package only needs to be extracted.

[**[COLOR=DarkRed]Download Modified ePSXe170 package[/COLOR]**]("http://www.mediafire.com/?1mg2lgmnmyn")

If you feel more secure obtaining the seperate downloads here are some links:

**[Download ePSXe170]("http://www.epsxe.com/files/epsxe170.zip")**

[[COLOR=DarkGreen]**Download OpenGL GPU**[/COLOR]]("http://www.pbernert.com/gpupeopsopengl178.zip") or [COLOR=RoyalBlue][**Download Soft GPU**]("http://www.pbernert.com/gpupeopssoftwin118b.zip")[/COLOR]

[[COLOR=DarkOrange]**Download zlib1.dll**[/COLOR]]("http://www.dll-files.com/zlib1.zip?0VJkUAWLgU")

The binaries you will otherwise have to obtain on your own unless you choose to use or copy them from the modified ePSXe package.

3. If you downloaded the modified ePSXe package then you simply need only to extract it and move to step four. Otherwise, if you've obtained ePSXe170.zip, a GPU plugin, and one or more bios binaries read the following. 

A.) extract the ePSXe.zip file.
B.) extract your GPU plugin(s) and place the contained .dll file(s) in the plugins folder inside the extracted ePSXe file.
C.) place your bios binary backup copy inside the bios folder of the extracted ePSXe file.
D.) place the zlib1.dll files inside the extracted ePSXe170 folder.

4. Open up your wine configuration menu. If you cannot find it by navigating your menu then:
```

winecfg # will work just as well

```After opening wine's configuration options first select the **applications tab**. You'll want to have "default settings" highlighted in the first menu. Next, where it says "Windows Version", I suggest using XP or Vista. Click apply and then navigate to the "Graphics" tab. This is where you may have to make some adjustments before things work properly. Right from the start, if you know you are using a lower-end graphics card and/or processor then you'll want to deselect the first box that says "allow directx apps blah blah blah.". Next select the other three boxes in the Window Settings section and for the bottom option in that section set the resolution to 800x600 (give or take based on your results). This will make ePSXe run from a window but the games will not lag or freeze up on you easily, if at all, because of lower-end hardware. However, if you're using a high-end system and you think your machine can handle it then you have two options. You can deselect the 1st and 4th box and select the 2nd and 3rd boxes in the "Window Settings" section...OR, if your screen went jumbo crayon on you like mine did then deselect all of the "window settings" section boxes and rock and roll. PS: you probably won't know how things will work out until you've configured ePSXe btw, so all of these most recent instructions are just a proactive heads-up... you'll thank me later for lessened grief ;)

5!... Now that all that is out of the way you're going to navigate the extracted ePSXe folder and if you've done everything like I instructed above, double-click or use the command-line to execute ePSXe.exe, and it will work.

6. You'll get a little ePSXe box and it will ask you to configure ePSXe. Go through and just select the bios binary you want and the GPU plugin (I hope you downloaded the soft plugin if you're using lower-end hardware). DO NOT ACTUALLY CONFIGURE ANYTHING EXCEPT THE CONTROLLERS. It will fail miserably, most likely, and it has absolutely no use on making this work. So clickity click your desired bios and plugins and next through that sucker. When you get to the cdrom section, play around with the two options until you get one that works. If you choose the correct option it will prompt you again and ask you to choose the exact hardware name of your cdrom/dvd drive (don't worry, it's autodetected and the only option :) )

7. Finally... you're done... You can play your PSX games now by selecting run and the appropriate option under the file tab. Choose cdrom for psx disks or backup disks, yes, ePSXe can run your backup copies! It can also run ISO's, MDS/MDF, and BIN/CUE files!. To use a backup file like mds or iso on your computer use the run ISO option, change the selection to allow you to view all files, and then select the appropriate iso,bin,mds, ect. and rock & roll. Note: if you experience lag using the cdrom option,ISO's,MDS/MDF's,BIN/CUE's, ect. type files on your harddrive run much...much faster 99% of the time.

[COLOR=DarkRed][B]UPDATE:

[/B][COLOR=Black]If you are using lower-end hardware and find that ePSXe is a bit laggy you can try this. Run ePSXe and then go to the config tab. click the video option. Switch your plugin to the soft plugin (soft plugin worked better for me) and then press config.  Now change your display resolution to a lower res. and then change the ratio/scaling option to scale picture to window size. You can allow window skipping if needed but can make the graphics kinda ugly. This will reduce some of the video quality but it will make most games run much smoother.[/COLOR]
[/COLOR]

---

### Post by dba_alex on 2010-07-11
I've been struggling to get this working all day, then I came across your post.

You're my new hero :popcorn:

---

### Post by d3v1150m471c on 2010-07-13
anytime mate

---

### Post by ultimatum_23 on 2010-07-16
[SIZE=2]Awesome guide d3v1150m471c!!! I've tried to compile from source many times with no success, kudos to you.[/SIZE]

---

### Post by d3v1150m471c on 2010-07-18
you're very welcome

---

### Post by slooksterpsv on 2010-08-24
Nice thread. Didn't know it was on here, my only comment is I actually use PCSXR and it works great! Haven't tried Wine yet, wonder how it works. I know I do have to disable composition to get good frame rates, how does Wine do with composition and frame rates?

---

### Post by d3v1150m471c on 2010-08-24
that's largely dependent on your hardware. my games run fine though

---

