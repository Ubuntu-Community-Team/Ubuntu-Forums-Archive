---
title: "Problems with moving to linux :O"
date: 2006-04-04
forum: General Help
---

### Post by tooleh on 2006-04-04
Okay, so I'm getting sick of having to pirate windows (poor college kid), security holes, etc, so every day I'm considering linux more and more.

Now, I've tried Mandrake and Fedora (ages ago), and have a SuSE distro that I never use...I've heard a lot of good things about it and I'm currently posting from the live install, which seems fairly nice :)

However, there are several problems:

1. Foobar2000 - no other player has catered for my needs - Amarok was close, but it didn't offer the configurability, nor the tagging support/database style I wanted. Fb2k is perfect for my needs and there's no way I'm going to change. I've followed foobar2000 development for a while and nothing else comes close to it.
(emulation a possibility? - can directsound/kernel streaming be emulated?)

2. 50 GB of MP3s (+60gb of other stuff) on an NTFS partition. There is no plausible way (as none of my mates would have space to transfer it) to get this onto another partition, unless I could safely convert ntfs to fat32 or something.
I tried captive-ntfs, which was okay until there was heavy usage (ie importing mp3 data into a playlist) and the driver died :S

3. I play games like Counterstrike (1.6) which uses Steam. I got steam working under Cedega in SuSE but I was getting about 20-40fps, which is not enough, as opposed to 60+.
Winex + steam?

4. I like the default MSN client and MSG+ - no linux clients do as well as it (not kopete, gaim), or have features that I like such as: - Personal messages, Display pics in contact list, video, file transfer, sound clips...etc.

5. Lots of API related things - atm I use the AMIP plugin for fb2k, which, for those that don't know, means that I can hit a hotkey to put the now playing track into whatever text field I'm in. Also it means I can hit a hotkey and a Jump To... dialog comes up (which is dead useful). Also, it means I have my currently playing track as my MSN Personal message.

6. I really really like my visual style. It is custom made and perfect for my usage.

7. I have a lot of fonts, for design work, I don't know how to get them from windows, to linux. I really really dislike the linux fonts as IMO they scale badly.

8. I could never get surround sound work, as I have a nForce2 chipset and a 4.1 speaker setup, which is damned weird.

9. I use photoshop/imageready a lot. I hate the GIMP.

10. There are many videos I watch in wmv or mov format.

11. There are many other programs that I am very very picky about, as I have tried many alternatives and settled with the one I like best, such as bittorrent client (utorrent), rapidget downloader, Media Player Classic, Blindwrite, Daemontools...too many to list.

12. I like lots of hotkeys - Winkey+D to minimize all, the buttons on my keyboard to control foobar, 

13. I dislike KDE :(

14. How themeable is gnome?

15. Media software such as Fruity Loops, I like to use. How do I make music on linux?

Would wine(x) really work for all of them? Would it be slower than running them on windows anyway?


Thanks, if anyone could take the time to look at all these and suggest things before I commit to installing ubunto :)


E: Okay for some reason rhythmbox isn't opening MP3s. I can't even listen to stuff while I await respone :(. Why?

---

### Post by ComplexNumber on 2006-04-04
the ones i know an immediate anser to are:

> 7. I have a lot of fonts, for design work, I don't know how to get them from windows, to linux. I really really dislike the linux fonts as IMO they scale badly. if you dual boot, you can drag and drop them across. besides, [here]("http://www.gnome-look.org/content/show.php?content=9883") are 6,700 fonts for you to take your pick, and [here ]("http://www.gnome-look.org/content/show.php?content=19259")are some ms fonts. to change the font settings, go to the gnome control panel.


>  13. I dislike KDE i don't blame you at all :p. it has its strengths and has many features that are better than those found in gnome, but overall, i don't like using it and i don't find it either reliable, comfortable, or predictable....amongst other things.

>  14. How themeable is gnome? its very themable. plus, it can be themed easily and *effectively*.  go to gnome-look.org for your themes (screenshots are provided).


>  15. Media software such as Fruity Loops, I like to use. How do I make music on linux? check [this]("http://www.hitsquad.com/smm/linux/") page out.

---

### Post by Schmung on 2006-04-04
Bloody hell Tool. Thought I was picky :p

MP3s etc, theres a restricted thread format. Licence not included with (k)ubuntu due to restrictions in certain countries. There be a guide you cna find to enabling the whole kaboodle if you search the forum for, I think, restricted formars.

There was a ditro of Linux aimed at music types on Distrwatcha a few days ago. Take a look at that, see whats included.

Scripts and so forth can be dumped into Gnome pretty easily for various things - f'rinstance running certain things as/with sudo.

Visual style is among the easier things to fix. Theres a truckload about - sure you can find what you want. Plus a load of extensions and the like that add functionaility.

Stuff converting NTFS - you can read direct from it, so your MP3 situation isnae a problem.

Photieshop/3DS MAX etc will all work via VMWare. 400 quid for a full copy. Sure you can find a solution to that one, though I've no clue how to isntall set it up yet as I am still strugling with wireless.

That should start you. Someone more knowledgeable than me should hopefully help you with the rest. Usual disclaimers RE my typing and blood/alcohol level apply.

---

### Post by karthik085 on 2006-04-04
Check under each question.

[QUOTE=tooleh]Okay, so I'm getting sick of having to pirate windows (poor college kid), security holes, etc, so every day I'm considering linux more and more.

Now, I've tried Mandrake and Fedora (ages ago), and have a SuSE distro that I never use...I've heard a lot of good things about it and I'm currently posting from the live install, which seems fairly nice :)

However, there are several problems:

1. Foobar2000 - no other player has catered for my needs - Amarok was close, but it didn't offer the configurability, nor the tagging support/database style I wanted. Fb2k is perfect for my needs and there's no way I'm going to change. I've followed foobar2000 development for a while and nothing else comes close to it.
(emulation a possibility? - can directsound/kernel streaming be emulated?)

Try Quad Libet.

2. 50 GB of MP3s (+60gb of other stuff) on an NTFS partition. There is no plausible way (as none of my mates would have space to transfer it) to get this onto another partition, unless I could safely convert ntfs to fat32 or something.
I tried captive-ntfs, which was okay until there was heavy usage (ie importing mp3 data into a playlist) and the driver died :S

Maybe Acronis Partitioner. Try seperating data from programs.

3. I play games like Counterstrike (1.6) which uses Steam. I got steam working under Cedega in SuSE but I was getting about 20-40fps, which is not enough, as opposed to 60+.
Winex + steam?

4. I like the default MSN client and MSG+ - no linux clients do as well as it (not kopete, gaim), or have features that I like such as: - Personal messages, Display pics in contact list, video, file transfer, sound clips...etc.

AMSN Messenger - MSN clone

5. Lots of API related things - atm I use the AMIP plugin for fb2k, which, for those that don't know, means that I can hit a hotkey to put the now playing track into whatever text field I'm in. Also it means I can hit a hotkey and a Jump To... dialog comes up (which is dead useful). Also, it means I have my currently playing track as my MSN Personal message.

If you want to use hotkeys, xbindkeys is one of many available options.

6. I really really like my visual style. It is custom made and perfect for my usage.

7. I have a lot of fonts, for design work, I don't know how to get them from windows, to linux. I really really dislike the linux fonts as IMO they scale badly.

Do a apt-cache search on fonts, fontname, etc.

8. I could never get surround sound work, as I have a nForce2 chipset and a 4.1 speaker setup, which is damned weird.

9. I use photoshop/imageready a lot. I hate the GIMP.

10. There are many videos I watch in wmv or mov format.

mplayer

11. There are many other programs that I am very very picky about, as I have tried many alternatives and settled with the one I like best, such as bittorrent client (utorrent), rapidget downloader, Media Player Classic, Blindwrite, Daemontools...too many to list.

utorrent works on linux. there are lot of linux alternatives in your list. you just have to search apt (enable universe or multiverse respo) or online and find a package that you like.

12. I like lots of hotkeys - Winkey+D to minimize all, the buttons on my keyboard to control foobar, 

13. I dislike KDE :(

14. How themeable is gnome?

Gnome has some good themes like clearlooks.

15. Media software such as Fruity Loops, I like to use. How do I make music on linux?

Would wine(x) really work for all of them? Would it be slower than running them on windows anyway?

Depends on how comfortable you are with wine.

Thanks, if anyone could take the time to look at all these and suggest things before I commit to installing ubunto :)

Try searching on ubuntuforums, google, etc.

E: Okay for some reason rhythmbox isn't opening MP3s. Why?[/QUOTE]

---

### Post by IYY on 2006-04-04
[QUOTE=tooleh]
1. Foobar2000 - no other player has catered for my needs - Amarok was close, but it didn't offer the configurability, nor the tagging support/database style I wanted. Fb2k is perfect for my needs and there's no way I'm going to change. I've followed foobar2000 development for a while and nothing else comes close to it.
(emulation a possibility? - can directsound/kernel streaming be emulated?)
[/QUOTE]

You could try it with Wine. I emulated Winamp quite easily, and while the GUI didn't show exactly right, the sound played perfectly. I don't know about similar software for Linux because I tend to use simpler players like XMMS.

> 
2. 50 GB of MP3s (+60gb of other stuff) on an NTFS partition. There is no plausible way (as none of my mates would have space to transfer it) to get this onto another partition, unless I could safely convert ntfs to fat32 or something.
I tried captive-ntfs, which was okay until there was heavy usage (ie importing mp3 data into a playlist) and the driver died :S


Well, Ubuntu can read NTFS partitions  (writing to them is buggy), but I don't really know how you'd manage this swap without another harddrive. 

> 4. I like the default MSN client and MSG+ - no linux clients do as well as it (not kopete, gaim), or have features that I like such as: - Personal messages, Display pics in contact list, video, file transfer, sound clips...etc.

There is aMSN. It's an MSN clone, but I find it to be quite clumsy.

> 6. I really really like my visual style. It is custom made and perfect for my usage.

Show us a screenshot, there could be a style similar to it for Gnome.

> 7. I have a lot of fonts, for design work, I don't know how to get them from windows, to linux. I really really dislike the linux fonts as IMO they scale badly.

You can use Windows fonts in Linux.

> 9. I use photoshop/imageready a lot. I hate the GIMP.

The GIMP is actually quite nice once you get used to it, but Photoshop can be easily emulated with Wine. I use it all the time.

> 10. There are many videos I watch in wmv or mov format.

I'm pretty sure you can view mov files (never tried) but wmv is certainly easy to get working. Just install the codecs and you're there.

> 11. There are many other programs that I am very very picky about, as I have tried many alternatives and settled with the one I like best, such as bittorrent client (utorrent), rapidget downloader, Media Player Classic, Blindwrite, Daemontools...too many to list.

Well, if you are really that picky about your software and are unwilling to change, you may find the switch to Linux difficult and even pointless. Emulation is nice if you're missing a program or two, but there's no point of trying to convert Linux to Windows. It'll never be as good at being Windows as Windows is.

> 12. I like lots of hotkeys - Winkey+D to minimize all, the buttons on my keyboard to control foobar, 

Can be done.

> 13. I dislike KDE :(

Don't use it. 

> 14. How themeable is gnome?

Very. Much more themable than XP. Look at art.gnome.org and [www.gnome-look.org](www.gnome-look.org).

> 
15. Media software such as Fruity Loops, I like to use. How do I make music on linux?

Audacity.

> Would wine(x) really work for all of them? Would it be slower than running them on windows anyway?

Maybe not for all. Certainly for some. Sometimes it would be slower, sometimes it would be the same. I've even seen cases where it was faster (Office 2000 on my machine).

> 
E: Okay for some reason rhythmbox isn't opening MP3s. I can't even listen to stuff while I await respone :(. Why?

You have to install the codecs. It's all in the Ubuntu Guide.

---

### Post by tooleh on 2006-04-04
Aha, thanks for the suggestions everyone.

aMSN - Nowhere near like MSN enough for my liking :/ It doesn't have a lot of the things I'm looking for and I just wouldn't feel comfortable with it.

Quad Libet - Can't find anything about this either on google or the ubuntu wiki?

With respects to partitioning - I have 100gb+ of non-application data on my secondary NTFS drive. There is no way I'm going to try resizing/moving it, as there's too much data and I don't want to lose it (these things are risky)

Cheers for the swift reply though :) I think I'll go ahead and overwrite my suse install, but will keep windows close-at-hand for incase I don't like it.

Thing about my windows setup was that many of my applications interoperated and were very specific to my needs. For apps such as Photoshop, MSN, Foobar2k, linux alternatives just don't cut it.

How easy are wine/winex/cedega to use?


E: I see another reponse:

Here's my windows setup:

[http://img.photobucket.com/albums/v142/Tool_Meep_Meep/desktops/2006-03-02.jpg](http://img.photobucket.com/albums/v142/Tool_Meep_Meep/desktops/2006-03-02.jpg) (note: winamp is pictured, however I use foobar now.

This is my foobar setup: [http://img.photobucket.com/albums/v142/Tool_Meep_Meep/screenies/fb2k_2006-04-03.gif](http://img.photobucket.com/albums/v142/Tool_Meep_Meep/screenies/fb2k_2006-04-03.gif)

- Are there are apps other than audacity? FL has some amazing stuff like Sytrus and Slicer and the sequencer and things.

Where can I find wine tutorials? Last time I used was a nightmare.

---

### Post by ComplexNumber on 2006-04-04
>  Quad Libet - Can't find anything about this either on google or the ubuntu wiki?

try [here]("http://gnomefiles.org/app.php?soft_id=561"). it gives the homepage too.

>  Where can I find wine tutorials? Last time I used was a nightmare.
try [this]("http://www.winehq.com/site/documentation")

---

### Post by tooleh on 2006-04-04
Ok I totally don't like quad libet's UI, which is a shame, as the features make it to look like a fairly nice app. -nothing- comes close to fb2k.

I'll check out the wine tuts, will begin installing in a bit.

Is there a Tango based theme/icon theme available for gnome?

Apologies for being so clueless and demanding :)

---

### Post by ComplexNumber on 2006-04-04
>  Is there a Tango based theme/icon theme available for gnome? metacity theme [here]("http://www.gnome-look.org/content/show.php?content=32390")
gtk themes [here]("http://www.gnome-look.org/content/show.php?content=34043").and [here]("http://www.gnome-look.org/content/show.php?content=33168"). another one [here]("http://tango-project.org/Tango_Icon_Library")
icon them [here]("http://www.gnome-look.org/content/show.php?content=31261"). there are other tango icons too for all theming needs, go to gnome-look
GDM theme [here]("http://www.gnome-look.org/content/show.php?content=34281").
splash [here]("http://www.gnome-look.org/content/show.php?content=34287").
any problems with how to install themes, post back.

---

### Post by danzat on 2006-04-04
I'm not saying your demands are unlegitimate, but it seems as though you want to move everything you have in windows to linux. In my opinion, this attitude is wrong.

Taking myself as an example, last time I used linux was about 3-4 years ago, and I was forced back to windows because of lack of software. I came back last week after seeing ubuntu at my friend's house, and after windows managed to cross my pain threshold.

The approach I took at first was to immediately look for software which resembled what I used on windows. But after a while I realized I'm being to square.
Over the 3 years of my absence, the Linux world has filled with tons of applications. I could actually for the first time pick an application to suit my needs.

Why should we be fixed on a design/gui/features that the world of windows dictated for us? You say you like you visual style from windows. I'm not saying that's wrong, but maybe linux has more features to offer you?

What I'm trying to say is, this is a "new world", you get to start over. Linux just might offer you what you always wanted but couldn't have (or even things you accepted as "impossible").

Don't try to rape Linux and force it to be windows, because it isn't.

---

### Post by chocolatetoothpaste on 2006-04-04
Well, you certainly have a lot of demands!  I don't blame you, as I like things very particular as well.  I would just suggest to you to find a linux distro you are comfortable with, and go for it head first.  I was very weary about switching fully to linux at first, since I had a lot of windows stuff I liked.  But then I just did it, and I love it.  The things is, we are only comfortable with the stuff we have, because a lot of us have been using windows for so long.  Maybe it is not that those things are what we like best, but maybe that was all that was available.  If you are looking for windows in linux, you will never find it.  You might come closer with Linspire.
  Anyway, if you are determined (like me) to get rid of the windows virus, you will simply find alternatives and cope.  Whether that alternative is through wine, or through the thousands of FREE apps that are available, there is a way.
BTW, I play wmv and mov files in Mplayer, and have perfect results.

Microsoft is digital communism!

---

### Post by IYY on 2006-04-04
> Microsoft is digital communism!

Well, actually Microsoft is digital capitalism with a monopoly, or maybe fascism. Linux is much closer to communism.

---

### Post by danzat on 2006-04-04
well, actually, MS is communism, because they are trying to bring everyone to the same level WHICH IS THE DEEPEST PIT OF HELL.

Linux on the other hand is very liberal, it allowes every user to live as he sees fit for himself.

---

### Post by tooleh on 2006-04-04
Haha, Linux is definately a more left wing OS, MS is fascism/capitalism in the same brew :P

But yeah, your philosophy of starting over is interesting, danzat - I'll check out what the scene has to offer and things before jumping to get winex working.

FYI, I'm using my new ubuntu install atm. And listening to MP3s on my mp3 player :X

But I'll go sort things out and post more questions in this thread ;D

Thanks for the help all, will check back laters.

---

### Post by tooleh on 2006-04-04
Okaay, got an error during compile saying I need some stuff:

./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for perl... /usr/bin/perl
checking for XML::Simple... configure: error: XML::Simple perl module is required for icon-naming-utils


Where would I get all the things I need to compile programs in general?


Also, howcome not all applications have themes applied to them?

And now I have a slight other problem:
[http://www.ubuntuforums.org/showthread.php?p=892064#post892064](http://www.ubuntuforums.org/showthread.php?p=892064#post892064)


Could this be due to .fon files?

How do I fix it? My OS is dead now :(

---

