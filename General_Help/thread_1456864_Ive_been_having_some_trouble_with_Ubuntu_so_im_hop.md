---
title: "Ive been having some trouble with Ubuntu so im hoping that some one can help me?"
date: 2010-04-17
forum: General Help
---

### Post by buntumax on 2010-04-17
I been trying yahoo                            *answers not getting not get*                           *answers. Anyway Im new to linux* well what I need help with is I cant find where my programs are installed(the folder like in windows its in my computer)I know how to open a programs ,document and media,so far all the windows programs I install(useing wine). I cant uninstall them,I cant find a Ubuntu version of pingin I go to the website for pingin go to the download page and in wont give me a download link and i look at other sites samethag and pingin is not in synaptic pack manager. the lest thag I cant  find a video converter or video/audio extractor,editor and you know anythag batter than avidemux that would be would be nice.im thankful for any help anyone will give me.

---

### Post by Georgia boy on 2010-04-17
Are you talking about Pidgin Chat? If so is it in your Repros? I know that it is in my 8.04 LTS. 

Tom

---

### Post by itiswhatitis on 2010-04-17
Pidgin is in /usr/bin on my install.

However, if you want to install programs

System->Administration->Synaptic Package Manager

You can mark packages you want here and unmark packages you want to remove.  Then click Apply and it all happens.

---

### Post by buntumax on 2010-04-17
Can anyone                            answer or my* Questions?*

---

### Post by Georgia boy on 2010-04-17
I did a Google and came up with some pages there for you to check. Maybe one of those will have what you are needing. Here is the link:
[http://www.google.com/cse?q=ubuntu+video+converters&sa=Search&cx=partner-pub-9300639326172081%3An71jpcz0370&ie=UTF-8](http://www.google.com/cse?q=ubuntu+video+converters&sa=Search&cx=partner-pub-9300639326172081%3An71jpcz0370&ie=UTF-8)

Hope it gives you some information.

Tom

---

### Post by oldos2er on 2010-04-17
Are you talking about pidgin or ping?

You can see where each file in a package installs to via Synaptic Package Manager; click Status, Installed, right-click on a package, Properties, Installed Files. Or in a terminal run ```
dpkg -L <package name>
```

---

### Post by 3rdalbum on 2010-04-17
Lots of questions!

Pidgin is in the repositories (Ubuntu Software Center) as long as you spell it correctly. If you still can't find it, try checking that the main, restricted, universe and multiverse repositories are enabled in the Software Sources program.

My signature has a screencast for telling you where to find programs that you've installed. If they are GUI programs they will show up in your Applications menu.

Kdenlive is a good video editor, it is also in the repositories.

---

### Post by Native Dialect on 2010-04-17
> **buntumax said:**
> what I need help with is I cant find where my programs are installed(the folder like in windows its in my computer)I know how to open a programs ,document and media,so far all the windows programs I install(useing wine). I cant uninstall them,I cant find a Ubuntu version of pingin I go to the website for pingin go to the download page and in wont give me a download link and i look at other sites samethag and pingin is not in synaptic pack manager. the lest thag I cant  find a video converter or video/audio extractor,editor and you know anythag batter than avidemux that would be would be nice.im thankful for any help anyone will give me.

1) Pidgin is the default messenger that comes packaged with Ubuntu. And it has been packaged with Ubuntu for some time. You can find it under Applications>Internet>Pidgin Internet Messenger. 

2)Programs installed through WINE, install to the following directory

~/.wine/drive_c/

3) If you want a really good video editor, you can download Kdenlive. It can be found in through the synaptic pack manager. 

4) You will have to be a bit more specific when you say video and audio extractor. The source you are trying to rip from, is important. E.g. your own DVD collection or CD collection etc.

---

### Post by 3rdalbum on 2010-04-18
> **Native Dialect said:**
> 1) Pidgin is the default messenger that comes packaged with Ubuntu.

Correction: Empathy is the default messenger. It's good. If you want Pidgin it's in the repositories.

---

### Post by buntumax on 2010-04-18
OK well I did get pingin to work.

---

### Post by buntumax on 2010-04-18
Yet I still cant find where all the program are  installed.

---

### Post by buntumax on 2010-04-18
I will try Kdenlive for video editing.

---

### Post by buntumax on 2010-04-18
I still cant figure out how to uninstall programs from wine and as far as extractor something like flv extract.

---

### Post by 3rdalbum on 2010-04-18
Your posts disturb me a bit; you're not telling us what you've tried already. Please, don't just say "I still can't figure it out"; tell us what you've tried already and what has failed (and tell us if you got any error messages).

Firstly, why do you need to know the file locations of the programs? What does it matter? If they're in your Applications menu, you can launch them. You can type their name into the terminal and they will run. It doesn't matter what the actual file location is, any more than it matters where on the disk platter it is stored. The operating system takes care of it for us - that's what an operating system does, it provides an abstraction so things are easier for users.

If you REALLY REALLY want to know where the programs are stored, then follow the screencast that is in my signature.

If you're talking about Windows programs, then they are stored in a folder called "drive_c" inside a hidden folder called ".wine" inside your home directory. You can remove those by going to Applications > Wine > Uninstall Wine Software, as I've already mentioned in an earlier post.

Kdenlive can extract audio tracks from videos, as can Audacity.

---

### Post by buntumax on 2010-04-18
Sorry for not making things more clear and disturbing you a bit. First ill try Kdenlive and Audacity. Anyway I did find where for the most part where windows programs are but when I try to use the wine application uninstaller about half of the programs wont show up and the other half when I click uninstall it will reinstall it instead. Anyway I did watch your video I know how to open programs but as where is the location is what I dont get and what I dont get is why has no one has made it simpler (I hate saying this but) like windows.

---

### Post by The Cog on 2010-04-18
When using wine, your windows programs presumably go somewhere inside the directory "/home/buntumax/.wine/drive_c/Program Files". .wine is a hidden folder (name starts with a dot) so you need to turn on viewing hidden files to find it.

---

### Post by ed-koala on 2010-04-18
If you want to simply convert avi files to DVDs, you can try Devede, its in the repositories.

Most program executable files - ubuntu programs - are in a bin directory, usually /bin or /usr/bin.  I wouldn't just delete them though to "uninstall" them, there's more to it than that. Best to use the apt command or Synaptic to add/remove programs.

Another place to look is /usr/share/applications.  Those are not the actual program files, but it does show some of what's installed just looking there.

---

### Post by camdude on 2010-04-18
I don't know what version of Wine your using, but I've used (both) the stable and the beta release, and all you have to do to uninstall a program (for ANY version of WINE) is go to -Applications-WINE-Uninstall Wine Software.

I hope this helps you!:)

---

### Post by itiswhatitis on 2010-04-18
Quick question, as I think I may be either misunderstanding or confused myself - probably both!  :-

Are you dual booting and trying to figure out where your Windows programs are for your actual Windows install?

---

### Post by buntumax on 2010-04-18
Ok First of all in the bin folder there are no folders (I repeat no folders) and like I said I cant uninstall any win programs useing wine. It wont let me.

---

### Post by itiswhatitis on 2010-04-18
> **buntumax said:**
> Ok First of all in the bin folder there are no folders (I repeat no folders) and like I said I cant uninstall any win programs useing wine. It wont let me.

I've use wine for a while and have not seen what you are describing.  Let's try the question a little differently?

Did you install the windows programs while you were booted into Ubuntu or did you install them while you were booted into Windows?

---

### Post by Native Dialect on 2010-04-18
> **3rdalbum said:**
> Correction: Empathy is the default messenger. It's good. If you want Pidgin it's in the repositories.

Perhaps that is the case for Karmic Koala, but I run Jaunty. And the default for Jaunty is Pidgin. The default for 8.04 was Pidgin. I don't think I've come across Empathy Messenger. Maybe that is a very recent shift :confused: If so, then my apologies for the unintentional misinformation.

---

### Post by buntumax on 2010-04-18
Wait I dont have Windows and I got pingin to work and as I said I got pingin to work> what I need help on is Windows programs (useing wine) wont uninstall and I can find where my programs are installed(the folder like in windows its in my computer)I know how to open a programs ,document and media.

---

### Post by The Cog on 2010-04-19
Open your home directory in nautilus, and in the View menu, enable Show Hidden Files. Then find the folder ".wine" and in there you'll find a folder "drive_c" and in there you'll find a folder "Program Files".

---

### Post by buntumax on 2010-04-19
Well I give up. I don't have the time or the care to keep dealing with this. I hate saying this but looks like I will have to switch back to Windows for now, at least until someone fixes these problems. For one make the file manager simpler or at least to make sense at all.  I do not like having to jump through all these hoops to make programs work and I don't like not knowing where they are installed to(the folder that they are in) and wine is well awful.  Ubuntu needs to be more simpler so the average user can use it and I don't like not having any control at all. Thanks for trying to help me anyway. If anyone fixes these problems I will try Ubuntu again.

---

### Post by Swagman on 2010-04-20
It's frustrating trying to do something in the way you always knew how to do it on a system that ***Doesn't*** do it that way isn't it ?

So you **MUST** forget the windows way or give yourself some time to adjust to the new way <--- That doesn't even need to be the Linux Way.

You didn't really give us any progress reports on our suggestions.

Below is a screengrab of my system, using the file manager **Nautilus** to locate the Wine directory.


[img]http://www.upload3r.com/serve/200410/1271772605.jpeg[/img]

---

### Post by buntumax on 2010-04-20
Well I did find the wine folder what I mean is I cant find wear any of my programs are installed to.

---

### Post by Native Dialect on 2010-04-20
They would be installed under, Program Files. I know that sounds sarcastic, but it really isn't. Anyways, if you are trying to uninstall games that you have installed through WINE, then you need to go under Applications > WINE and then look under the apps there. You should see the traditional Windows based uninstall wizard.

---

### Post by oldos2er on 2010-04-20
> **buntumax said:**
> Well I did find the wine folder what I mean is I cant find wear any of my programs are installed to.

You've been given several suggestions in this thread. Could you be more specific about what exactly you've tried, and what went wrong? Being vague makes it difficult to help.

---

### Post by buntumax on 2010-04-21
What do you mean [FONT=Arial]I find my files any of them.[/FONT]

---

### Post by buntumax on 2010-04-21
I mean I cant find any of them.

---

