---
title: "Make a windows only all-in-one work on Ubuntu 11.04?"
date: 2011-04-09
forum: General Help
---

### Post by ClientAlive on 2011-04-09
I have an HP j4680 all-in-one that the manufacturer says does not work with Linux. I gather that what he meant though was that they don't make drivers specifically for Linux. I know that the driver discs I have are two discs - one for Windows and one for Mac. This thing has wireless capability. I also remember that, when I was running Windows XP, this disc would install all kinds of extra programs like an HP store and a monitor that would, I think, collect usage data, and all kinds of useless stuff. When I had tried to uninstall these extra things I'd run into all kinds or problems using the printer.

Well, anyway, I was just wondering if there is a way to use my printer again now that I'm running Ubuntu 11.04. It would be nice to use the wireless capabilities of it too.

Thanks,
Jake

---

### Post by coffeecat on 2011-04-09
I'm posting from 11.04 right now. Despite what HP says it seems as though the driver for your machine is included - if you mean the **OfficeJet** j4680. See my screenshot. It should work just fine.

[ATTACH]188571[/ATTACH]

---

### Post by ClientAlive on 2011-04-09
Yes Officejet j4680 bought about 6 or 7 mos ago.

Maybe I should have tried this first, or maybe what I just did just complicates matters when it comes to using some of the functions. Since I'm so new to Ubuntu I'm still learning how to find some of the things I need and work with it.

I'm reading Ubuntu Unleashed; and, right after my initial post, I noticed a section on configuring a printer. It suggested that Ubuntu might just detect and install it for me. So I went ahead and plugged it in (through USB) and turned it on. It did detect it and I was able to print a test page via system settings and then into the printer's properties - but I notice that there is a check mark next to the icon for this printer (even when I had it plugged in through USB) and the option to set as default is not available in the drop down. In Windows that is usually what the check mark means. Also, "Enabled" (in the dropdown when you right click the printer's icon in system settings) is not marked when I am not plugged in through USB.

So I'm wondering a couple things. (1) Will it be possible to use this printer wirelessly; and, if so, what can I do to get this working? And (2) could it be that the driver being used right now is not the proprietary HP driver and maybe has only limited functionality? I opened additional drivers just to see what might show up but it didn't come up with anything more.

Any thoughts on this?

Thanks,
Jake
:)

---

### Post by coffeecat on 2011-04-09
System Settings > Printing. The green checkmark means that it is the default. I guess that you cannot change that because it is your only printer. I have three printers set up and I can change the default by right-clicking on the icon of the one I want as default and choosing 'set as default'.

I believe the driver that comes with Ubuntu is from the hplip set, so it should be fully functional. What is useful is to install the package hplip-gui which is a GUI utility that complements HP printers nicely.

I have no experience of setting up a wireless printer but this is what you do for a network printer. Unplug the USB cable and then click on "Add" in the Printing window. Wait a little while and it will autodetect a network printer and you will be able to follow the wizard. However, that will only work with a wireless printer if you have configured it with your WPA/WEP passkey so that it can connect to your router. How you do this, I do not know. Perhaps via USB and hplip-gui, but I don't know. Perhaps someone else will.

Good luck!

---

### Post by ClientAlive on 2011-04-09
Awesome. Thanks! I'll look into setting the printer up with my router. Seems like I remember having to do something like that under Windows before but there was an app for it then. Maybe I can do it through the printer itself. I'll look into that app you mentioned too and see what it's about.

Have a great day.

Jake

---

### Post by jerome1232 on 2011-04-09
I'm about 99% sure setting up your printer for wireless can be done from it's front panel, my officejet 6500 (not wireless but ethernet) let's me change it's dhcp options and everything from the printer itself, and has a little web server built into it so you scan via your web browser.

This is why I love hp, very linux friendly :)

---

### Post by ClientAlive on 2011-04-09
Ok. So I found this video tutorial online:  [http://h30460.www3.hp.com/?fr_story=FRdamp359033&rf=sitemap](http://h30460.www3.hp.com/?fr_story=FRdamp359033&rf=sitemap)  and followed the guy's instructions up to the point where I have configured the printer to my router through the printer's control panel and printed out the "Network Configuration Page". This portion ends at about the half-way point in the video.

After this he is talking about Windows and installing drivers (or something) for it via the installation cd. I already have some driver installed that works with my Ubuntu 11.04 when I'm plugged in through USB. This is the one that came when I plugged the printer into the computer and turned it on earlier (post #3 in this thread).

Now, the gist of what the guy in the video tutorial is talking about in that second half - is to configure the printer on the computer for wireless. What I attempted - but was very careful about making any kind of changes or going too far - was going into "Add to Group" in the right click drop down menu. The closest I was able to get to anything that made sense was a place to add "device URI"; and, on the "Network Configuration Page" I had printed there is an entry that gives me the "URL" but "URI" and "URL" are not exactly identical in spelling and so I went no further.

I believe that what I need to do is configure this printer through the computer's settings for wireless but I'm not sure how to go about this (if the option is even available). I don't want to make a mistake and configure it for a network if that is something different.

Thanks.
Jake

---

### Post by jerome1232 on 2011-04-09
So the printer has succesfully connected to your router correct? You should be able to just automatically find the printer and add it using the add printer utility.


Can you browse to the printer's ip address (found on that network config sheet) in your web browser?

---

### Post by jerome1232 on 2011-04-09
Some clarification


edit:

According to this : [https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)

It might be better to run hp-setup so

```
sudo apt-get install python-qt4
sudo hp-setup
```

Goto System-Administration-Printing, Add Printer, Network Printer, Find Network Printer, type in you printers ip address and go from there.

---

### Post by ClientAlive on 2011-04-09
> **jerome1232 said:**
> Some clarification
Goto System-Administration-Printing, Add Printer,  Network Printer, Find Network Printer, type in you printers ip address  and go from there.

Ok. Did that and was able to print a test page at the end of that process. Was not plugged in through USB so it had to have done so wirelessly. I wanted to be sure that everything was on the up-and-up though so I opened a document I had created earlier to test the system by printing it.

What I found out was (1) That printer was not set as the default and I needed to go in and do so. I did. (2) that, in Libre Office Writer at least, clicking the printer icon in the toolbar seems to send the document to the other printer even thought the wireless configured one is/ was already set to be the default printer.

What I mean is that I now have 3 printers showing. They are all referring to the same physical device: one is the printer, set up from earlier, that works only when plugged in though USB, the other is the fax of the same, and finally, the printer set up wirelessly.

So then, If I use the menu to submit the print job: file > print > ok then it will print wirelessly. If I use the printer icon in the toolbar some window pops up and then dissapears so fast I can't begin to see what it is; and then I find out that the job is in the que for the other printer (the one set up to be plugged in) - but the wireless one is the default printer. Maybe this is a bug in Libre. I don't know.

Thanks for your help.

Jake

---

### Post by jerome1232 on 2011-04-09
It might help to remove the usb printer since you shouldn't need it anymore.

---

### Post by ClientAlive on 2011-04-09
Yup! That worked. Thanks Jerome.

Now the one last thing I would like to do is add the fax wirelessly as the printer is now. Tried to go through the same process thinking I might get a dropdown that lists the fax but it just does the same thing as when I added the printer - I canceled out of it. I also tried to put it through as "other" but that doesn't get me anywhere at all.

Thanks
Jake

---

### Post by jerome1232 on 2011-04-09
I would actually remove all intsances of the printer and use the hp-setup method I describe in post #9.

I'll actually fiddle with mine I'm sure ours are very similar I've just never messed with the fax.

edit: Yup just confirmed that, ran the hp-setup utility and I can send documents to the fax.

---

### Post by ClientAlive on 2011-04-10
Thanks Jerome, but, what it talks about at that link in your other post sounds a lot like what I did to begin with (plugging in the printer and having it detected automatically). I'll have to look into this more but I think I would first like to try and find a way to configure it (the fax) manually. Might take me a bit to get to it (I have 4 or 5 other things I'm into with this computer right now). I think I have a pretty good handle on what needs to happen though. If something else comes up I know where to turn. You guys are great! Thanks.

Jake

---

### Post by jerome1232 on 2011-04-10
??

Nah, just install python-qt4 and run sudo hp-setup. It will find the printer and setup xsane for scanning from it, setup the printer and the fax for you.

I think you are reading all the parts that don't really apply... since your using it wirelessly there's no reason to be messing with any usb cables. 

So ***all*** you have to do is:

```
sudo apt-get install python-qt4
sudo hp-setup
```

 And stop messing with the usb cable!

Good luck with getting everything else working.

---

### Post by ClientAlive on 2011-04-10
This sounds great Jerome but may I ask one quick thing before I _execute_ those instructions? (That was a joke - 'execute' ha ha). :grin:

So anyway, I wonder if doing that will undo any of the other things that  are set up so far; or, in what position it will leave me. This is no  problem whatever. It is fine. I just wonder if I will end up with  multiple instances of the printer again and have to delete one and/ or  if I'll have to configure the wireless to my router again, etc.

I suppose I can just do it though and figure it out then. Not a huge biggie.

Thanks.

Jake

------------------------------

First results:

~$ sudo apt-get install python-qt4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-qt4 is already the newest version.
python-qt4 set to manually installed.
The following packages were automatically installed and are no longer required:
  libsc-data libsc7
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.


I think that what that is telling me is that, that package was already on here so it didn't do anything (except tell me it was already there)? What I'm not so sure about is where it says it is set to manually installed.

Thanks
------------------------------

---

### Post by jerome1232 on 2011-04-10
Since you have the printer added once already, I think it will add it a second time and you'll need to delete one (preferably the one you added)

That's it.

---

### Post by ClientAlive on 2011-04-10
Oh wow. Back to square one. Not working wirelssly even though during setup it connected and I was told it went through fine. In the printer's properties it says the status is stopped or unplugged. When I click add to check out if it's on the network it shows up in the list.

I'm prob going to have to delete everything and do it the way I did yesterday. If I can find a way to add the fax manually after that - great. If not, oh well.

Thanks.

Jake

----------------------

In addition to the above. I then restarted the computer and checked printer's properties again. No change to status. I then restarted printer and checked properties again. No change to status. Tried to print a test document. After a couple min and no response I opened the print que and saw the job sitting there "pending." Canceled the print job. Here I am.

Not a big deal. It's all a learning experience. Maybe whoever reads this thread down the line will be helped by it.

Be blessed

---

### Post by jerome1232 on 2011-04-10
Ok, sorry hp-setup didn't work out for you. Good to know that it isn't the one stop miracle for hp that I thought it was.

I do however think I know how to manually add the fax. When I go through that add printer utility, if I let it sit for a bit after selecting network printer thinking it populates my printer into the list, After selecting my printer on the right hand side of the screen towards the bottom there's this little drop down arrow that says "connections", if you drop it down you can select "HP Fax".

See my screenshot (the resolution is terrible because my graphics card literally melted the other day, I'm waiting on the new one atm)
That's what I get for OC'ing it I guess.

---

### Post by ClientAlive on 2011-04-11
Right on. I'll see if I can find a few minutes tomorrow to work on that. Well see how it goes (fine I'm sure).

Not sure what OC' ing something means (OH!! Over Clocking?). Anyway, sounded funny from an outside perspective. Not so much for you though, I'm sure. Sorry.

Jake

---

### Post by ClientAlive on 2011-04-11
Ok. Got it. Thanks Jerome - and everyone else. It was a little tricky since, at first, my printer was not showing up in the list when I went into add like that. I think it may have been because I somehow ended up with more than one instance of the app opened at the same time - I don't know. I went ahead and closed system settings down (all opened windows of it) and restarted it and my printer showed up in the list in add then. I was then able to follow the instruction you gave me in post #19 to manually add the fax.

Attachment shows what it should look like in Ubuntu 11.04 (for anyone who may read this thread in the future).

Sincerely.
Jake
:D

---

