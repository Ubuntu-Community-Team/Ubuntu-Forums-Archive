---
title: "How get languages to run + everything including settings,printerdriver into isoimage?"
date: 2010-10-21
forum: General Help
---

### Post by ambeginnersearchinginfo on 2010-10-21
First I give a short description what we tried, then I put our questions.

Problem: How to get to run the languages using a live system without a hard disc?

We use Kubuntu live 10.04, because it is said to support many languages.

What we did:

First we got a burner programm and the isoimages 10.04 for CD and DVD on a hard disc of a windows system and burnt a CD and a DVD.
Then we tried both CD and DVD to set in the KDE different system languages and keyboard layout languages and to write languages.
In both cases we got a message that the languages are not completely in the isoimage and we started the download of the missing packages. The CD version interrupted the download with an error message. It does not work.
We continued with the DVD and could successfully complete the doemload.
We could write different languges, but not Korean, Japanese and Chinese.
We could change the system language to Korean, but the setting of the keyboard layout didn't give any Hangul/ Korean Characters, only Latin.
We tried many things and ask somebody knowing quite well
without any success. We tried to toggle/change/switch between Eenglish and Korean using right alt key and tab key, but a friend told us, that an input into a Korean web site typing on the keyboard as it would be a Korean keyboard, was accepted by the web site as the correct Korean input, but the letters that appeared on the screen as the echo of what  was typed on the keyboard, was still Latin/English.
Therefore we think it is not a problem how to switch between English and Korean.

We are stuck with the Korean and didn't try everything for the Japanese and Chinese,
we got some Kana but no Chinese characters.
 
But wenn we tried to select a fifth languge keyboard layout, we got a limit and had to remove another one. That is very disappointing!

 Questions:

1) How to get an Korean keyboard echo, that means that the characters which are typed on the keyboard, appear on the screen as Korean characters?

2) How to increase the limit of four selected keyboard layouts.
    In Windows we can select more than a dozen.
    Why it is not possible to select any number of keyboardlayouts?

3) We have approximately 5 GB left unused on the DVD.
    Why there are not all language packages in the DVD isoimage and are there
    any DVD isoimages containing all language packages available for free download
    in the internet?

4) we want to use a live system without a hard disc or other drive,
     and it is not convenient every time after switching the computer on
     loosing much time for downloading everything and repeat all the settings
     we are using.
     We reviewed information in he internet, and it is said that there are tools
     to convert an isoimage into a folder of files and vice versa.
     But the information is too general.
     When we are in the KDE at the place where to select the system language,
     we get a pop up and we can select whether or not we want to download the
     missing language packages. Then several hundred files are downloaded, but
     we don't know where they are in the computer and how to get them into the folder
     for composing the isoimage and we don't know where in the folder for composing
     the isoimage they have to be copied. The same is true for the Mozilla and for the
     printer driver. And the description of these utilities does not say anything how
     to get the settings into the isoimage. It is annoying to begin everytime to select all
     the keyboard layouts, the system language and so forth. We need more concrete,
     precise, accurate information.

     How can we get all the language packages, the Mozilla, the printer driver and all
     our settings into the isoimage?

5) We don't know where and how to make an suggestion. So we write it here.
    Maybe somebody can send it to the appropriate place.
 
    Suggestion: to offer on the official download site also an isoimage with
    all language options or even better:
   
     If there is an utility to convert a folder into an isoimage,
     then there could be a folder on the official download server,
     which contains all and everything and all and every language
     and everything else which is free and downlaodable for using in ubuntu.
     And there could be a Gui selection menue where you can select all the option
     and languages and files and drivers and so on and and and...
     Then the server can copy all the selected files into another folder and an utility
     converts the folder into an isoimage sends it for download to the computer,
     where the selection was made. This could work automatically and everybody
     gets what is needed or desired.
     This would make it much easier for many user to install and use the system.

---

### Post by kumaryu on 2010-10-22
The "Live" CD or DVDs are read-only. You cannot save changes onto it. LiveCDs are primarily intended to demonstrate the features available. Putting every conceivable drivers and applications on an iso would not be practical from space considerations (std CD-R = 650-703MB).

1. In order to save user data, settings and downloaded applications, you need to set up up "Live CD Persistence" (You will need a USB stick):
[https://help.ubuntu.com/community/LiveCD/Persistence#Setting](https://help.ubuntu.com/community/LiveCD/Persistence#Setting) 

2. In order to correctly install language input features,
[http://ubuntuforums.org/showthread.php?t=1595258](http://ubuntuforums.org/showthread.php?t=1595258)

3. The instructions above are for Japanese under Ubuntu (not Kubuntu) but other East Asian languages use the same framework (Ibus). Install one language, check to ensure that its working properly before installing further languages.

4. Yes there does appear to be an arbitrary limit of 4 keyboard layouts in Xorg XKB. I think this is common to all Linux distros with Xorg/X11 GUIs.

---

### Post by ambeginnersearchinginfo on 2010-10-22
Thank you for the answer. We need some time to review it.

---

### Post by ambeginnersearchinginfo on 2010-10-24
We want to use a read-only DVD, that is what we want.
And we have approximately five GB free space on it, so don't worra about the space.
We want to use a live system without any persistent memory, that is what we want.
Thank you for the link [https://help.ubuntu.com/community/Li...stence#Setting ,]("https://help.ubuntu.com/community/LiveCD/Persistence#Setting")
it conains information about producing an isoimage. We will review it.
The link [http://ubuntuforums.org/showthread.php?t=1595258](http://ubuntuforums.org/showthread.php?t=1595258) ,
give information for the settings in ubuntu 10.10 for japanese.
We didn't yet understand it completely, we are using kubuntu 10.04.
But because we can write many language, it might not be a problem of the setting process, 
but some special concerning the Korean keyboard alyout or what ever.
But the control space we didn't know, so we will check it.
We will open further threads because what appears to us as a problems might appear to others as seperate problems and peaople knowing about it might find it better.
Again thank you for your answer.

---

### Post by kumaryu on 2010-10-25
"We want to use a read-only DVD, that is what we want.
And we have approximately five GB free space on it, so don't worra about the space.
We want to use a live system without any persistent memory, that is what we want."

You may also want to look at this article:
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

It discusses how you can incorporate additional packages into a LiveCD iso. Persistence of configuration changes and installed applications will still be an issue however since both CD-R and DVD-R are read-only. In order for the changes to be retained after a reboot, you will need to use a USB stick or other writable media.

---

### Post by ambeginnersearchinginfo on 2010-10-27
Thank you very much for the answer!
There are some settings which we will use in generel. If we could get them in the isoimage would be very nice and sufficient. We don't want to have any persistent memory. 
I will review the link later. 
At the moment I am stuck. I can't get Korean characters on the screen. 
This is the first problem we have to solve.
In the other thread I wrote:
<<
Thank you for your answer!
Do you mean the right Alt key also called Alt Gr key by saying "Han/Yeong" key?
I reviewed the thread and I understand, that you can indeed write Korean characters,
is this correct?
I am already trying to get Korean characters (hangul) on the screen using keyboard input for several months without any success, only English. Even if I have Korean system language and Korean  keyboard layout as the unique keyboard layout without any English  keyboard layout I get only English. I tried everything, Kubuntu 10.04,  kubuntu 10.10, I read what ibus and ispell is, what the menue key etc.  is,tried all key combinations mentioned anywhere, found ibus as chosen  etc., but no result, only English. And there is so little information  about language input in ubuntu/kubuntu on the intternet.
I have no idea what the problem is. I can write Japanese Kana and I tried many other languges successfully, but Korean won't work.
I don't know, why  other languges work and if   I do the same thing in order to get Korean there is no effect, only English. I use Kubuntu and KDE.
I would kindly ask you to give a detailed explanation how did you manage to get Korean characters on the screen by typing on the keyboard.
Thank you very very much!!!
>>
I understood, that the author of the other thread wrote that Korean characters could be put in and appeared on the screen. I hope very much, that we will get a hint what the problem is, when we review the hopefully detailed description of installing and/or selecting the settings, which we will get hopefully.
Thank you very much.

---

### Post by kumaryu on 2010-10-27
You appear to be having a number of different but probably related issues. I would therefore suggest the following.

1. Do a clean installation of Ubuntu (not Kubuntu) using the English language Ubuntu LiveCD (10.04 or 10.10). By a "clean" installation, I mean installation onto a hard disk. 

I suggest this for a number of reasons. 
a. Ubuntu and IBus combination is more widely used than Kubuntu. Wider usage means that there would be more people able to assist in case you encounter difficulties.
b. There appears to be some minor issues with Kubuntu and IBus on 10.10. (see: [http://ubuntuforums.org/showthread.php?t=1603019](http://ubuntuforums.org/showthread.php?t=1603019) )
c. A hard disk installation will allow you to properly test the installation and subsequent changes in a standard environment. Once this is completed to your satisfaction, you can start considering CD/DVD and persistence.

2. Once you have a working instance of standard Ubuntu (in English), use:
Menu: System>>Administration>>Language Support>>Language.
to select "IBus" as the input method.

3. To install Korean, goto Menu: System>>Administration>>Language Support>>Language>>Add/Remove languages >>Korean.
(Make sure "Input Methods" and "Extra Fonts" are selected but not "Translations")

Install only one additional language for now.

4. From Menu: System>>Preferences>>Keyboard Input Methods>>IBus Preferences>>Input Method:
select Korean from the drop-down menu and add it to the list of input methods.

5. From Menu: System>>Preferences>>Keyboard Input Methods>>IBus Preferences>>General:
select "Show icon on the System Tray" and "Show Input Method Name..".

6. Choose "restart" from the Keyboard menu on the system tray.

If all goes well, this should allow you to change input methods from a floating language bar  on the desktop.

---

### Post by ambeginnersearchinginfo on 2010-10-27
Thank you very much for the information.
At the moment I can't burn, Iwill later burn a ubuntu CD,
but I guess there is no Kde and it looks a little different.
So I don't understand immediately, what you are writing,
I have to see how it looks like.
But there is a question.
Do I have to reboot the computer,
what do you mean to restart,
In a live system things will be erased and also
we have to change languages frequently,
it is not usable if we can not change languages by just one or two clicks.
Imagine you are writing a vocabulary list and for every line you have to change the language several times. And you have a limit of only four languages in your language selection list. That would not be usable and changing in Kubuntu I can change between the languages without booting, I only cannot write Korean maybe also not Chinese and Japanese Kanj. And this should work.
So do we have to reboot or restart the computer in ubuntu?
If I choose Russian, I don't have to reboot, why for Korean?

In the other threa you mentioned I have the following question ( it is a copy from there):


Sorry, I have a couple of basic questions.
In Kubuntu 10.04 in the KDE I click the first botton left  and then I find system settings.
Clicking on that leads to a window with a variaty of options, where I can click languages.
Then I can chose between keyboard layouts and the menue for selecting  the system language. But I don't understand, where exactly the ibus  should show up. Could you please describe, where exactly where the ibus  is. Thank you very much. 
Sorry for not understanding.
Is panel the very bottom of the screen also called task bar
and the system tray its right side also called notification area?
What is the language Panel? Is it where is written EN for English and KO  for Korean and so on, where you can click on it and switch between  maximum four languages?
What is *ibus-qt4* and [I]ibus-gtk.

[/I]I use Mozilla and I read that iibus-gtk is used by Mozilla.
Do I have to download it and from where?
I searched on Ibus page but didn't find it.
But there I found a ibus-hangul, what does this mean?
It says:<<
It is a Korean input engine for IBus.>>
Do I have to download this also?

I didn't find the ibus but there was a search function in Kubuntu, I entered 'ibus' and something showed up on what I could click.

Thank you very much!

---

### Post by kumaryu on 2010-10-27
**A, Installing Ubuntu:**
I very very strongly recommend that you "install" Ubuntu (or Kubuntu) rather than attempting to use it directly from a LiveCD (or DVD). Although you can possibly achieve what you want using the "LiveCD Persistence" method I introduced in the previous post, it is not something I can recommend for requirements such as yours.

Is there any compelling reason why you MUST use a system from CD-R or DVD?

**B. IBus and Keyboards:**
"Restart" mentioned in the previous post is for restarting IBus, not the computer.

Once the input method engines (IME) have been installed in IBus, you do not need to restart the computer (or IBus) to switch languages.

IBus is only needed for languages that require input method engines (IME). The number of characters, and/or the selection/transformation of the glyphs usually dictate this.  Examples of languages requiring IMEs include but are not limited to: Chinese, Korean and Japanese.

There appears to be a limit of 4 IMEs in IBus. (this requires confirmation)

Languages using the Latin or Cyrillic alphabets, such as English, French or Russian, typically do not require IMEs and therefore do not use IBus.

Languages that use the latin alphabet may be added by adding the relevant keyboard configurations. (But this is more to do with matching the layout on physical keyboards. When typing in French, you don't need to use the French keyboard layout (AZERTY). You only need to know how to invoke the various vowels with accents.)

Languages that use the Cyrillic alphabet may be added by adding the relevant keyboard configurations and additional fonts for the particular language. You would probably need a Cyrillic keyboard though.

**C. Panel/Task Bar**
By "panel" I mean the task-bar or tool bar area that may be found along the bottom and/or the top of your screen. In Kubuntu, this is normally found at the bottom of the screen. On Ubuntu, there are panels at the top and the bottom.

System tray and Notification Area are both modules (or applets) on the Panel that show icons or notifications from various installed applications. In Kubuntu, this is normally found on the  right-hand side. In Ubuntu, this is normally found on the top panel.

As long as your PC environment and IME/IBus have been set up properly, most, if not all major applications (such as Mozilla Firefox) will be able to utlise the new input methods.

---

### Post by ambeginnersearchinginfo on 2010-10-27
Thank you very much for your information.
I learned a lot and it is getting clearer.

Sorry, I have no own computer.
I have to use the computers according to the rules according to which they can be used.

I write blind using ten fingers. I don't need any Korean or other characters on the keys, they could be blanc.
But you write that it is possible to add layouts and fonts. 
What do you mean by saying that. How can I add keyboard layouts and fonts, having a limit of four languages?

I would be very happy if you could tell me where exactly in which menue at which place in KDE/Kubuntu I can find ibus.

You helped already a lot!
Thank you very much!

I copied the text from the next page under this text, so you don't need to move to the next page.

The discussion leads to the idea, that maybe it is necessary to download further stuff,
e.g. something called 'ibus-hangul' or other stuff. Maybe this is the problem.
What do you think?

Is there a Korean forum or maybe a mirror in Korea having a downloadable functioning Korean Kubuntu system isoimage?

Where is a list of the mirrors or how to find them.
How can I download from there.
I was on the official homepage for kubuntu and there is just a botton for download and it downloads from an arbitrary place not indicatable.

---

### Post by ambeginnersearchinginfo on 2010-10-27
erased. the text moved to the former reply.
I don't know how to erase a reply not being necessary.

---

### Post by kumaryu on 2010-10-28
Ok, I think I now understand enough about your situation.

**1. Korean Ubuntu team Forum is here:**
[INDENT][http://ubuntu.or.kr/](http://ubuntu.or.kr/)[/INDENT]
(errr... Apologies. This should have the very first thing to recommend)

**2. Use a USB stick to keep changes to your system.**
Here is a simple set of instructions for creating a persistent  Ubuntu environment on a USB stick:
[INDENT][http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/#more-2322](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/#more-2322)[/INDENT]
The instructions are for 9.10 but it should be applicable for other releases. Instructions for Kubuntu here:
[INDENT][http://www.pendrivelinux.com/create-a-kubuntu-9-10-flash-drive-from-cd/#more-2577](http://www.pendrivelinux.com/create-a-kubuntu-9-10-flash-drive-from-cd/#more-2577)[/INDENT]

(Perhaps this is my own personal bias, but I do believe that there are more users of Ubuntu (with IBus) than Kubuntu (with IBus). This being the case, I would recommend using Ubuntu since more eyeballs mean better support.)

**3. IBus**
[INDENT]a. IBus is not needed for all languages.
b. IBus is not required for Western European or Cyrillic scripts.
c. IBus is required for languages that need an IME (Input Method Engine)to input.
d. IBus is required for: Chinese, Japanese and Korean (and others).
e. IBus works with specific IMEs for each language.[/INDENT]

**4. List of the most common CJK IMEs for IBus:**
[INDENT]Chinese: Chewing
Japanese: Anthy
Korean: Hangul[/INDENT]

**5. IBus Prefs in Kubuntu**
[INDENT]a. Right click on the K menu.
b. Select "Switch to Classic Menu Style" (there are 2 menu styles: "Classic" and "Kickoff")
c. Left click on the K menu.
d. Select: Settings >> "Keyboard Input Method"[/INDENT]
This is only available if IBus has been properly installed.


In addition to CJK, which languages do you need to work with??

---

### Post by ambeginnersearchinginfo on 2010-10-28
First of all thank you very much for your information and the links.
I am feeling as I get slowly a better understanding,
and again I learned a lot.
I understand what you are saying about ibus and ime.
At the moment I try to find out where and what to select
and the most interesting information for the time being is number 5).

I have no scrennshots, so I describe what I see.
I put the Kubuntu-CD 10.04 in the drive and start the computer.
After waiting for a long time an English system will be working with 
a screen having a botton in the lower left corner.
Clicking on this leads to a row of several bottons,
the most right one serves to switch the compuer off,
the second from the right serves as a history.
Then clicking on the first or second from the left
leads to a window ( I guess it is called pull down menue or something like that)
with several options/programms,
e.g. on the top of the window when clicking on the first botton from the left side
is the KDE browser.
Then I select something called like system settings.
Is this that, what you mean by saying settings???????????????????????????????
I think this is an important question for me. I think I get a guess, where the problem could be. 
Then I click on system settings and open the system settings window
which contains a huge number of options.
What I did in 10.04, was I entered the languages option.
In 10.10 however the keyboard layouts weren't anymore with the languages option, but I found something with the keyboard option.
Now it gets very important, because maybe that is part of the problem.
Now you go into the languages option or you don't go into the languages option, but in another option?????????????????????????????????????????????????????
?????????????????????????????????????????????????????????????????????????
?????????????????????????????????????????????????????????????????????????

If I have to go into another option in order to get Korean, than without any doubts I can not get the Korean Characters.
I always went into the languages option, thinking that the language settings would be performed in the languages option and indeed, for most languages it was the case.
If you are saying that for Korean I have to go into another option,
than this might be the problem.
So this would be a very important answer, I guess!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Incidentally I found another thread dealing with Korean,  but I think this is also Ubuntu:

[http://ubuntuforums.org/showthread.php?t=1489023&page=5](http://ubuntuforums.org/showthread.php?t=1489023&page=5)
.
First I think I should solve the problem getting Korean input.
Then I try to get Chinese characters in Korean language.
Next languages will be Japanese and Chenese.

Thank you very much!

---

### Post by kumaryu on 2010-10-28
5. IBus Prefs in Kubuntu

a.** Use the RIGHT mouse button to click **on the K menu.
b. Select "Switch to Classic Menu Style" (there are 2 menu styles: "Classic" and "Kickoff")
c. Left click on the K menu.
d. Select: Settings >> "Keyboard Input Method"

---

### Post by ambeginnersearchinginfo on 2010-10-28
Thank you for the answer.
When I get the CD again, I will check the right click
inform you about the result. 
Thank you.

---

### Post by ambeginnersearchinginfo on 2010-10-31
First of all,  thank you very much, it worked for Ubuntu 10.10. 
( the problem of installing and writing languages is solved so far,
remaining the four language layout limit and how to get it into the isoimage,
I will open spezial threads for that.)
Here I have windows and I don|t know how to get in windows Japanese on the screen, so I will thank you in Japanese later on.
I tried Kubuntu,
very slow, 
the language packages loading very time consuming,
then it get stuck during the loading or if not,
the screen turns black and I have to restart the computer,
so I burned an Ubuntu 10.10 CD.
It is pretty fast and I could get all languages and also Chinese characters in Chinese, Japanese and Korean so far.
I don't know what is with the KDE.
(I also right clicked and found the ibus, but it seems there are problems with the KDE.)
In Ubuntu 10.10 a botton was called slightly different than in the description,
but I found it.
Ubuntu 10.10 does not enter automatically into the live system but waits for a decision
of the user.:(
And the four languages limit remains also un ubuntu.:(:(:(:(:(:(:(
Installing Korean as system language, keeps some English remaining.
Did I something wrong or is not everything translated?
I think the window of the language support window is a little narrow.
I think for the 4 languages limit by-pass, I will open another thread.
At the moment there are very good informations on 
[http://ubuntuforums.org/showthread.php?t=1607208](http://ubuntuforums.org/showthread.php?t=1607208)
concerning a possible py-pass.
First I have to learn how to find things in Ubuntu.
One easy question:
Could you please tell me how I find the terminal in Ubuntu and how can I return from the terminal back? I might need it for finding a by-pass four the limit problem.
Thank you.

---

### Post by ambeginnersearchinginfo on 2010-11-06
Language input seems to work now, at least for the languages I tried so far.
I found the terminal in the left pull dpwn under the upper first entry.
I quit the terminal by closing its window, but I don't know, whether this is the appropiate method for quitting the terminal.
Workarounds for the four keyboard layouts limit, the printer driver problem and how to get everything into the isoimage I will discuss in seperate threads.
I say thank you very much to all of you and for all the help!!! 
&#47588;&#50864; &#44048;&#49324;&#54633;&#45768;&#45796;.
&#12393;&#12358;&#12418;&#12354;&#12426;&#12364;&#12392;&#12358;&#12372;&#12374;&#12356;&#12414;&#12375;&#12383;&#12290; 
&#35874;&#35874;!

---

