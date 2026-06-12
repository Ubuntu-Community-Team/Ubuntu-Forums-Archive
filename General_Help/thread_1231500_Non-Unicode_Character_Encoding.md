---
title: "Non-Unicode Character Encoding"
date: 2009-08-04
forum: General Help
---

### Post by Tofu_Madness on 2009-08-04
Where can I change the encoding option for non-Unicode characters? For example in Vista, under the Language Options and the Administrative tab I can pick and choose the encoding option for non-Unicode character (in this case, Korean). Is there anything equivalent in Ubuntu?

[IMG]http://img18.imageshack.us/img18/7418/nonunicode.png[/IMG]

Much thanks in advance!

---

### Post by Tofu_Madness on 2009-08-04
OK. So I guess I wasn't clear enough. Maybe that is why no one has replied to this thread yet... 

So, basically I am having trouble displaying non-unicode characters, Korean to be specific. When viewing non-unicode Korean characters I get weird symbols and sometimes black diamonds with questions marks in the middle. Now, I don't have problem displaying unicode characters. No blank rectangles or rectangles with four number and letter combination. Nothing like that.

At first I thought I was just missing some essential Korean fonts. But in the process of installing some popular Korean fonts, I realized that Ubuntu was having difficulty displaying some of the file names and realized the problem was with non-Unicode characters.

[IMG]http://img44.imageshack.us/img44/5733/screenshotrfp.png[/IMG]

For example, above files should say something like &#45208;&#45588;&#44256;&#46357; (Nanum Gothic), etc.

Anyways, I poked around and only solution that I could find was for Windows Vista (I was having similar problem in Vista). I just need to change the default character encoding to EUC-KR or something like that. EUC-KR is what I have on Firefox for character encoding.

Well, any help is appreciated!

EDIT: I just realized EUC stands for extended unicode.. so I guess my title is wrong! :D

---

### Post by tonydesu on 2009-08-26
Yeah, I have the same problem. I hope someone can help! I also need help with support for Korean.

---

### Post by The Cog on 2009-08-26
Edit: Earlier comment withdrawn. For some reason, I couldn't see the attached images earlier.

Where were the font files acquired from? If from a disk-type media (USB stick for instance), you can specify the filesystem charactersetas a mount option (assuming you know it). If from unzipping a zip file or similar, then I really don't know.

---

### Post by oldmankit on 2010-03-08
This problem also applies to me.  I am trying to run software in wine which uses non-unicode Thai.  In XP it is easy to get it to display correctly: download microsoft app-locale and run this program using Thai encoding.

I'd love to be able to do the same in ubuntu.  Currently I have to crank-up virtualbox every time I want to use my Thai dictionary.

---

### Post by oldmankit on 2010-03-08
I'm a little bit excited here...I've found a fix.  My language is Thai (th_TH TIS-620)

First you need to add the locale, see: [http://code.google.com/p/winelocale/wiki/AddLocalesToDebian](http://code.google.com/p/winelocale/wiki/AddLocalesToDebian)

You can test that it has worked by typing ```
locale -a
```You should see your new encoding at the bottom of the list.  I successfully added the above encoding, though it only displays as th_TH (without the TIS-620 bit).

Then to run your program in the console like this (replacing 'th_TH' with whatever encoding you are using):

```
LC_ALL=th_TH wine ~/.wine/drive_c/windows/notepad.exe
```Hey presto, notepad with Thai menus!  How it translates from English to Thai I don't know, but it's very clever.

The final step for me is just to get prettier Thai fonts.

---

### Post by eng.pctec on 2010-05-12
I have almost the same but with Arabic language:
I have UBUNTU 10.04
and I installed Wine on it
I have a windows program "dictionary" I runt it on wine and it's working but the problem is that the Arabic letters are shown as "?????" like in the picture:
[IMG]http://img101.imageshack.us/img101/390/screenshotthedictionary.png[/IMG]

Usually, I face the same problem when using this software under windows, but the solution is by going to the "language settings" and choose the Arabic language for the non-unicode programs, but in UBUNTU I found no such choice.

I copied the windows fonts to the home/user/.wine/drive_c/windows/fonts

but the problem didn't solved

Any one can help please

---

### Post by oldmankit on 2010-05-13
> I have almost the same but with Arabic language

Did you try the fix I posted?

---

### Post by eng.pctec on 2010-05-16
Well ... the result of the "locale -a" is:
ar_AE.utf8
ar_BH.utf8
ar_DZ.utf8
ar_EG.utf8
ar_IN
ar_IQ.utf8
ar_JO.utf8
ar_KW.utf8
ar_LB.utf8
ar_LY.utf8
ar_MA.utf8
ar_OM.utf8
ar_QA.utf8
ar_SA.utf8
ar_SD.utf8
ar_SY.utf8
ar_TN.utf8
ar_YE.utf8
C
en_AG
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NG
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX

As u see, there is a lot of Ar_something .. and one of them is Ar_SY which is the language I need

U Said that u found the encoding u need which is "th_TH TIS-620" but how did u know it? how can I know the encoding I should add?

and .. really thank you for your effots

---

### Post by oldmankit on 2010-05-17
Hi,

First check that you can open the program using wine (that the path is correct):
```
wine path_to_your_dictionary_program.exe 
```It should open but with the wrong encoding.

Then you can test one of the encodings from that list:

```
LC_ALL=ar_SY.utf8 wine path_to_your_dictionary_program.exe
```However, it's my guess that a unicode encoding won't work.  So you'll need to register a non-unicode Arabic encoding.  I had a look around.  ISO-8859-6 might work.  I'm not an expert, so if the following doesn't work, maybe someone else can help!

In the terminal, type:
```
gksudo gedit /var/lib/locales/supported.d/ar &
```Give it your sudo password.  Add this line somewhere: ```
ar_SY ISO-8859-6
```Then close gedit.  Then:
```
sudo dpkg-reconfigure locales
```Then finally
```
LC_ALL=ar_SY.ISO-8859-6 wine path_to_your_dictionary.exe
```

---

### Post by eng.pctec on 2010-05-19
When I'm trying the following:

wine wine /opt/SakDictionary/DIC32.EXE

I'm getting this message:

[[img]http://www.freeimagehosting.net/uploads/1f071b0219.png[/img]](http://www.freeimagehosting.net/)

any way ... I added the ar_SY ISO-8859-6 to the Locales file, I opened the program but with the same problem

I tried to do this code:

LC_ALL=ar_SY.ISO-8859-6 wine /opt/SakDictionary/DIC32.EXE

but I got the same error message:

[[img]http://www.freeimagehosting.net/uploads/1f071b0219.png[/img]](http://www.freeimagehosting.net/)

I'm new to this, so I'm just following your steps, sorry for not being so creative ! and thank you again

Waiting your replay

---

### Post by oldmankit on 2010-05-24
I don't know what 'cannot open group file' means, but I don't think it's anything to do with languages.  I would fix this problem first before going on with the languages thing...

> **eng.pctec said:**
> wine wine /opt/SakDictionary/DIC32.EXE

You've typed 'wine' twice there.  

Do you have this trouble with any other windows programs?  Someone else may need to chip in here...

---

### Post by eng.pctec on 2010-05-30
Dear Mr. OldManKit

I can't express my grateful to your kindness !

Let's continue

When I tried to open the dictionary like:

~$ wine /opt/SakDictionary/DIC32.EXE

I got the following message:

[[img]http://www.freeimagehosting.net/uploads/1f071b0219.png[/img]](http://www.freeimagehosting.net/)

Any way, I copied the "ar_SY ISO-8859-6" to my Locales and reloaded them as u suggested, but when trying again to open the dictionary:

~$ LC_ALL=ar_SY.ISO-8859-6 wine /opt/SakDictionary/DIC32.EXE

I got the same message:

[[img]http://www.freeimagehosting.net/uploads/1f071b0219.png[/img]](http://www.freeimagehosting.net/)

I tried to open the dictionary directly by double clicking on the DIC32.EXE but still the same problem!

Regards

---

### Post by oldmankit on 2010-06-16
Hi,

Sorry, for delay, I've been on holiday!  

If you get an error by typing
```
~$ wine /opt/SakDictionary/DIC32.EXE
```then you need to fix that first, before trying to fix locales.  I would recommend you first search and then start a new thread in the wine forum ([http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)).  Once you've fixed that, go on to sorting out the encoding problem.

Good luck!

---

### Post by ainshtin on 2012-01-05
this may useful for you
[http://ubuntuwd.com/vb/archive/index.php/t-707.html](http://ubuntuwd.com/vb/archive/index.php/t-707.html)

the following was useful to me 
{
right click on file>Properties>Open With>Add button
then
>use a custom command 
 and write

gedit --encoding=WINDOWS-1256

then click add

try open file again
 }

---

