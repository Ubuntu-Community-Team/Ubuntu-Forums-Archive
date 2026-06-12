---
title: "flash player wont work"
date: 2012-10-13
forum: General Help
---

### Post by tobythedog on 2012-10-13
hi i have been trying to get the flash player to work on my pc with lubuntu , i have been trying for months to get this working.so far with absolutely no success, i normally like to use opera , i am using 11.52 as i seem to have display problems using any more recent version.i cannot get flash to work with opera or firefox.i also hove the chrome browser which comes with lubuntu this doesnt work at all just keeps crashing.
It is such a pain not having the flash player working ,i must have spent hundreds of hours trying to get it to work its so frustrating , any help would be appreciated.

---

### Post by BlueBinary on 2012-10-13
Hello TobyTheDog,

         If you have trouble installing flash, you can use the ubuntu software center. Even though your are using Lubuntu you can just download/install it from the Synaptic Package Manager that comes default on lubuntu.

       Hope this helps :D

---

### Post by Frogs Hair on 2012-10-13
Try this add-on with Firefox. Opera will be able to use the installed Flash Player also . 
[https://addons.mozilla.org/en-us/firefox/addon/flash-aid/](https://addons.mozilla.org/en-us/firefox/addon/flash-aid/)

---

### Post by TenPlus1 on 2012-10-14
Open a Terminal window and type the following:

   sudo apt-get install adobe-flash-properties-gtk

This will install Flash 11.2 as well as the gtk control panel for it...

---

### Post by tobythedog on 2012-10-14
tried all that doesnt work

---

### Post by tobythedog on 2012-10-14
still no luck i get error saying   Unable to locate package adobe-flash-properties-gtk

---

### Post by Pilot6 on 2012-10-14
Flash 11.2 does not work on cpu's with no sse2 support (Pentium III, AthlonXP, etc).
To get flash working on old comps you should download flash 10.3 from adobe.com. Then extract libflashplayer.so and copy it to /usr/lib/flashplugin-installer.
Package flashplugin-installer must be installed before.
You can also freeze flashplugin-installer from updating using Synaptic.

---

### Post by tobythedog on 2012-10-24
how do i extract and copy it please not much good at computers need more detailed description of what i need to do , i think my laptop is athlon processor.

---

### Post by Pilot6 on 2012-10-24
1. Download this [http://download.macromedia.com/pub/flashplayer/installers/archive/fp_10.3.183.29_archive.zip](http://download.macromedia.com/pub/flashplayer/installers/archive/fp_10.3.183.29_archive.zip)
2. Double click this file.
3. Open 10.3.183.29 folder
4. Open flashplayer.....linux.tar.gz

You'll see libflashplayer.so file. Copy it to your home folder.
Then open termindal and run the command

sudo cp ~/libflashplayer.so /usr/lib/flashplugin-installer/libflashplayer.so

Restart browser and flash will work. 
Then you need to use Synaptic and prohibit this package from being updated.

---

### Post by Locus Kiesselbachi on 2013-01-19
> **Pilot6 said:**
> 1. Download this [http://download.macromedia.com/pub/flashplayer/installers/archive/fp_10.3.183.29_archive.zip](http://download.macromedia.com/pub/flashplayer/installers/archive/fp_10.3.183.29_archive.zip)
2. Double click this file.
3. Open 10.3.183.29 folder
4. Open flashplayer.....linux.tar.gz

You'll see libflashplayer.so file. Copy it to your home folder.
Then open termindal and run the command

sudo cp ~/libflashplayer.so /usr/lib/flashplugin-installer/libflashplayer.so

Restart browser and flash will work. 
Then you need to use Synaptic and prohibit this package from being updated.

Hello!
Im somewhat new to Linux.

I made forum account specialy to say "thank you" for TobyTheDog for setting up a question/problem and Pilot6 for finding solution. 

So this is my first post.
I have also AMD Athlon processor, which is for now almost decade old.
I used many hours to understand what exactly am I doing wrong, I suspected CPU might be a problem, but didnt find any logical link to it.
Before this thread I bumped in Adobe bug report page, where was many ranting about new flash release not supporting older CPU-s (with Linux?)
Then i found out about non-SSE2 CPU-s.  :´(

Anyways for others with same problem, pay attention to admin rights in Linux if you are "loged in automaticaly", it doesnt let you copy that .so file to "/home" just like that, need to "sudo" it in terminal. It is somewhat riddle for newcomers to understand these "commands", but dont give up!

Would it be nice if someone would do a special flashplayer package for non-SSE2 CPU-s in Synaptic? 
There are some so called "restricted-packages for firefox", but didnt help for me, because they get newest plugins (I think?).

After flash worked, I was somewhat disapointed of my old computer, because I tought light-Linux would make flash videos more "faster"/non-slide-show. That means only one -  capacitors in motherboard are getting old.

Im have Lubuntu (Oneric Ocelot). Newest Ubuntu/Lubuntu has Installation problems with AMD processors (only common thing I could find), (probably that non-SSE2 problem again, who knows... :-) ).

How to exactly freeze updateing Flash? Pilot6?

---

### Post by mastergunner on 2013-01-29
I have tried this method and it is still having issues. My CPU is an Athlon XP-M

---

### Post by Locus Kiesselbachi on 2013-02-09
> **mastergunner said:**
> I have tried this method and it is still having issues. My CPU is an Athlon XP-M
Can you be more precise about "issues"?
Make sure you carefully run through instructions given in this thread!

---

### Post by Locus Kiesselbachi on 2013-02-09
mastergunner!
What browser do you use?

*I noticed flashplayer works only in Firefox_(18.0.1), but does not in Chromium_[COLOR=#303942][FONT=Ubuntu][COLOR=Black](23.0.1271.97-0ubuntu0.11.10.1).

So glitch still remains somewhat.[/COLOR]
[/FONT][/COLOR]

---

### Post by mastergunner on 2013-02-09
I now have flash working using and old version. I do have a few problems though. How do I disable the "outdate flash" warning in Chromium? how do I get rid of the choppy play in flash? How do I lock this version of flash in Lubuntu so it will not be updated? Thanks to the help this forum provides because I would be lost without it.

---

### Post by Locus Kiesselbachi on 2013-02-10
> **mastergunner said:**
> I now have flash working using and old version. I do have a few problems though. How do I disable the "outdate flash" warning in Chromium? how do I get rid of the choppy play in flash? How do I lock this version of flash in Lubuntu so it will not be updated? Thanks to the help this forum provides because I would be lost without it.

Yes, old version seems the only choice regarding Flashplayer, until some reliable alternative comes in future (I hope from Linux community).

Yes, indeed it works also in Chromium (my mistake in brevious post)
*To allow outdated plugins in Chromium:
Right click on Chromium application shortcut ...and IN **"command"** box make sure you have "**chromium-browser --allow-outdated-plugins**" (without"") after last "slash"(/). normally theres somekind of "U%" or something like that.

*I locked flashplayer in _Synaptic package manager_ (at least I think I did):
search: "flashplugin-installer"
select: "flashplugin-installer"
In upper toolbar "Package", select "Lock Version"! - Im not sure tough, it shows version 11, but Flashplayer is v10.
Just in case I turned off all updates in "Update Manager", until somebody more experienced looks over my post. Im really tired of this trial and error... I have reinstalled Lubuntu several times already (some other reasons).
Still waiting answer from Pilot6... 

Isnt Linux a hassle... LOL
):P

---

### Post by Locus Kiesselbachi on 2013-02-10
About choppy play in Flashplayer... sorry, but to me it seems that this program IS power_hungry little b*st*rd.
I recommend using Flash**block** in Firefox, becouse some webpages has lot of Flash eyecandy and commercial-ads. Flashblock allows you to choose what to activate.

I can surely blame old hardware, as in time condensers/capacitors lose their capacitance over time  ... it makes computer slow. Cheaper hardware decrades faster... SO ...is cheapest always THE cheapest in longer perspective? Electrolytic-capacitors (mostly_used) lose their performance within 5 years, Tantalum-capacitors are very expensive, but last almost eternity ...in theory. Old capacitors can be replaced by soldering.

---

