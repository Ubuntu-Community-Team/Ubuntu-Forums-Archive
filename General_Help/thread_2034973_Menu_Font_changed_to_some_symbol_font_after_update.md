---
title: "Menu Font changed to some symbol font after updates"
date: 2012-07-29
forum: General Help
---

### Post by cosbear on 2012-07-29
Howdy:

My menu font has recently changed to some symbol font. I thought at first it was Chinese or some Asian Font, but actually it looks more like some symbol or machine language font. I'm running Xubuntu 12.04, with lightdm. It is a recent install, and everything was working perfectly. I have not changed any personalization of menus, styles, or fonts. They were the same as they were at install. I recently had some updates, and later that day I noticed that nearly all of the entries in all my menus had changed to this unintelligible--to me anyway--font. So except for the most used entries, in the most used menus I don't know what any of them are. Not all entries in the menus are in this font, some are still in english, sometimes mixed with the new font. It's not exclusively menus either, the weather app on my taskbar also shows characters where it should say Temp and Hum. 

In the main menu all entries are the symbol font, but when you go to the sub-menus, some are english and some are symbol.  In the file manager Thunar, all of the contents of directories are in english but some of the Left side pane entries and all the menus are in the symbol font.

I have tried to find some way to change the setting that controls which font is used for menus, but can't figure it out because I don't understand any of the menu entries, and don't want to screw anything else up. I will put a new install of xubuntu in a vm and try and use the vm menu entries and screens in a vm window to compare with the entries and screens with these symbol ones on this install in hopes of finding what settings to change to fix this. 

Other than this one problem, everything else is working perfectly and is perfectly functional. This is a serious problem though. The only personalization that is not app specific which I have changed from the stock settings is the taskbars and taskbar icons. I have a large number of apps that are not in the original installation installed and fully configured; as well as, wine and wine apps and VBox with several vms, so I would hate to have to start over with a new install. It would probably take nearly a whole day to do, if I have to.  I have searched seriously, thinking that someone else must have also had this problem but have found no forum listings about it. At first, because I noticed the change shortly after updates I figured it was the result of some update. As I have found no forum entries about this problem however, I am unsure that it is related to the updates. If anyone has any ideas for a fix I would greatly appreciate some help. Thanx for your kind attention to this matter. Later...cos

---

### Post by Toz on 2012-07-29
Can you check (or probably try to change) the "Default Font" setting located in Settings Manager -> Appearance -> Fonts tab? I get a similar effect if I change the font to Wingdings.

---

### Post by cosbear on 2012-07-29
> **Toz said:**
> Can you check (or probably try to change) the "Default Font" setting located in Settings Manager -> Appearance -> Fonts tab? I get a similar effect if I change the font to Wingdings.

I tried that, and I think it was the Appearance/Fonts screen and changing of the fonts in any of the gadgets doesn't seem to make a difference; though it's so hard to tell because everything in the menus and screens in Settings manager is in this strange font. Also I have looked through all the fonts on my machine, and not one of them listed anywhere is the one used in the menus. So I can't identify it or send an example. 

I'm no expert on these kind of scripts, but it is similar to chinese in that each character is a sort of pictograph with more than one symbol in it. Some of the symbols are the same or similar to symbols I have seen on various mahjongg tiles. I guess i'm going to have to do a new install on a vm, to help me by comparison to navigate the screens and menus in settings, and also compare responses to changes I make. I don't have the time for that, but will have to find it, I guess. Thanks for your suggestion. Later...cos

---

### Post by cosbear on 2012-07-29
It seems that more than just the menu items in this font are changed. All system messages are, many things in apps, and all the dialogs and menus in the VirtualBox control panel are all in this weird font. Even worse none of my virtual machines will boot, nor can I install a new vm from a xubuntu install disc or iso file. In all cases I get a error message from VirtualBox which I have never seen before. The error message is:  AMD-V is disabled in the bios. (VERR_SVM_DISABLED). This message comes up for all the old vms and any new ones when I try to boot them. So VBox is completely disabled for all intents. I'm stymied on this one as I assume that the bios referred to must be the bios for the virtual machine rather then the system bios on my motherboard. I have no idea how one changes the bios for a VBos vm, nor what settings to change if I did. It's beginning to look more and more like I must wipe my hard drive and reinstall from scratch to solve this. What a bitch. If anyone has any ideas I would sure appreciate hearing from you. Later...cos

---

### Post by Toz on 2012-07-29
> **cosbear said:**
> It seems that more than just the menu items in this font are changed. All system messages are, many things in apps, and all the dialogs and menus in the VirtualBox control panel are all in this weird font. Even worse none of my virtual machines will boot, nor can I install a new vm from a xubuntu install disc or iso file. In all cases I get a error message from VirtualBox which I have never seen before. The error message is:  AMD-V is disabled in the bios. (VERR_SVM_DISABLED). This message comes up for all the old vms and any new ones when I try to boot them. So VBox is completely disabled for all intents. I'm stymied on this one as I assume that the bios referred to must be the bios for the virtual machine rather then the system bios on my motherboard. I have no idea how one changes the bios for a VBos vm, nor what settings to change if I did. It's beginning to look more and more like I must wipe my hard drive and reinstall from scratch to solve this. What a bitch. If anyone has any ideas I would sure appreciate hearing from you. Later...cos
Actually, it would be the bios of your computer. Look for a similar setting and make sure that it is enabled.

---

### Post by Toz on 2012-07-29
> **cosbear said:**
> I tried that, and I think it was the Appearance/Fonts screen and changing of the fonts in any of the gadgets doesn't seem to make a difference; though it's so hard to tell because everything in the menus and screens in Settings manager is in this strange font. Also I have looked through all the fonts on my machine, and not one of them listed anywhere is the one used in the menus. So I can't identify it or send an example. 

I'm no expert on these kind of scripts, but it is similar to chinese in that each character is a sort of pictograph with more than one symbol in it. Some of the symbols are the same or similar to symbols I have seen on various mahjongg tiles. I guess i'm going to have to do a new install on a vm, to help me by comparison to navigate the screens and menus in settings, and also compare responses to changes I make. I don't have the time for that, but will have to find it, I guess. Thanks for your suggestion. Later...cos

Did you add language support or change the default language? If possible, can you run the following commands in the terminal and post back the results:
```
cat /etc/default/locale
cat ~/.pam_environment
```

---

### Post by cosbear on 2012-07-30
Howdy Toz:

Here is the response to those queries: 

cosbear@Home:~$ cat /etc/default/locale
LANG="en_US.UTF-8"
cosbear@Home:~$ cat ~/.pam_environment
LANGUAGE=zh_CN:en
LANG=zh_CN.UTF-8
LC_NUMERIC=en_US.UTF-8
LC_TIME=en_US.UTF-8
LC_MONETARY=en_US.UTF-8
LC_PAPER=en_US.UTF-8
LC_NAME=en_US.UTF-8
LC_ADDRESS=en_US.UTF-8
LC_TELEPHONE=en_US.UTF-8
LC_MEASUREMENT=en_US.UTF-8
LC_IDENTIFICATION=en_US.UTF-8

Not sure what that means exactly. Looks like it's set to english, but I'm not sure what UTF-8 means. I did not add any language support or change the default lanquage settings other than the ones asked for referring to language and keyboard settings asked by the system installer at initial installation. I will check the system startup and see what bios settings might of changed. Thanx for your input. Later...cos

---

### Post by cosbear on 2012-07-30
Howdy:

I don't know for sure yet if I can call this solved, but my english menus are back. You were right it was a system bios setting in the startup that was causing VBox problems. I reset it and now it functions as normal again. I also noticed that there was an icon on my taskbar that I had never seen before. Turned out it was an ibus icon. I used synaptic to look up Ibus and all of the chinese and korean fonts and deleted all of the things related to it. Then I went to logout to restart the display and log back in as myself. When the chooser came up, I noticed on the bottom that there was a gadget which had chinese displayed in it, so I clicked it and it offered different languages. So I set it to english american and logged back in. When it came back up my english menus were back and so far everything seems to be working right. I can't say that the issue is solved because I'm not sure what caused it or which thing that I did fixed it. Nor can I say for sure that it is totally fixed. It's a big improvement though for sure.

I do know that I had recently had some reason to logout and back in recently around the time this all started. I noticed this morning when I was in chooser that after changing the language from chinese to english when I went to put in my password I used the number pad. Rather then entering my passwd, because the number lock that enables the keypad was off, no passwd was entered but each time I pressed a number on the keypad the entry in the language gadget changed and by the time I entered my passwd it had changed back to chinese. So I reset it to english and then entered the cursor to the passwd slot, hit the number lock button and then entered my passwd successfully and language was still set to english, so I clicked on login.

My guess is that I started all of this when I logged out and back in several days back and unintentionally changed language setting in chooser without noticing it because the number lock was not set. Just a guess, but it sounds likely. I'm pretty sure now that this problem was not caused by the recent automatic updates. 

Not sure if my deleting the Ibus stuff will cause other problems or not. If it does I know what I deleted and can reinstall if necessary. So I guess I caused this myself by being in a hurry and not watching what I was doing carefully enough. No big surprise. Well hopefully I haven't screwed anything else up, mucking about in chinese menus. If I have, I'll wipe my hard drive and install over when I have a little extra time.

The bios issue which was causing VBox not to work I think is a problem which may be related to this machine being dual booting with win7. It may be that some bug in windows caused a problem with my bios settings, causing me to recently reset the cmos because of problems with booting. I will do a comprehensive security and virus scan in win7 and make sure there is no problem there, then I am going clear the cmos and reflash the bios to the newest one before doing anything else. It appears I had more than one problem going on at the same time and they were not necessarily related to each other. Seems odd that something in Win7 would have changed the cmos, but it's a possibility, something caused it. I hardly ever use win though and never go online with it, and have good virus protection and security on it. I am closer to a solution to all these problems than I was yesterday, and I can live with xubuntu now until I have time to reinstall if I have to. Thanx a bunch for your input Toz. Later...cos

---

### Post by JKyleOKC on 2012-07-30
Take a look in Software Center or Synaptic for the program "localepurge" which can be run to remove all the locales you don't need from your system. If you install it, it will run each time you update the system, and remove all the material that comes along to support languages that you have configured it to discard.

Using the keypad for any part of logging in isn't a good idea, since the NumLock state gets toggled several times during system initialization and you really can't tell what it is at that point. On my system, the LED gets out of sync with the state itself at times...

---

### Post by cosbear on 2012-07-30
> **JKyleOKC said:**
> Take a look in Software Center or Synaptic for the program "localepurge" which can be run to remove all the locales you don't need from your system. If you install it, it will run each time you update the system, and remove all the material that comes along to support languages that you have configured it to discard.

Using the keypad for any part of logging in isn't a good idea, since the NumLock state gets toggled several times during system initialization and you really can't tell what it is at that point. On my system, the LED gets out of sync with the state itself at times...

Thanx for the tip JKyle, I'll check out localepurge. Yeah, I guess you are right about the number pad. I never have used chooser all that much, mostly just on very rare occasions I had to log in as root. Never even noticed a language selector on there before, might be new to the latest version of xubuntu. I am not sure. Sure is weird how the number pad changes the language if numlock is not on.

I checked out my win7 install and it did have a virus. I couldn't find out that much about the virus, but did get rid of it. Then I downloaded the newest bios update, then cleared and updated the bios. Don't know if the virus I killed could have changed my cmos or not but something had to do it. Darned windows. Well the good news is that my 4 core AMD processor had the option with the new bios to unlock the cores, which is something I had been wanting to do, so now the cores are unlocked, and performance is better than ever. I may even try some reasonable overclocking now, as the overclocking possibilities have changed with the new cmos. It's all good, though it was a perplexing head scratcher for a few hours. Learned some new stuff and that's always good. Hopefully everything is fixed now. It all seems to be working perfectly so far. Later...cos

---

### Post by JKyleOKC on 2012-07-30
> **cosbear said:**
> Sure is weird how the number pad changes the language if numlock is not on.Here's my guess: your password contains at least one of these digits, 2, 4, 6,and 8. When NumLock is off, those keys correspond to the arrow keys. 2 and 8 are up and down while 4 and 6 are left and right. The login program interprets the arrow keys much like the tab key, to move from one input area to another, and as you tried to input your password, those arrow-key equivalents moved your input area from the password box to the chooser list, then up or down in the list until it landed on Chinese.

You could test this by using the arrow keys at the password entry area.

The equivalence dates back to 1981 and the very first IBM PC, which did not have separate arrow keys on its keyboard. They made the number pad serve double duty. The other digits are 0=insert, .=delete, 1=end, 7=home, 3-PageDown, 9-PageUp, and 5 has no equivalent. The arrow keys did not appear for several years, at about the same time that Function Keys 11 and 12 showed up.

---

