---
title: "Why the separate application (Catfish) for searching files?"
date: 2012-05-19
forum: General Help
---

### Post by Manmadegod on 2012-05-19
When I mentioned that I wanted to change my default file manager from Thunar to Nautilus, and that among the reasons was that you can search files with Nautilus, I was told it is recommended that I use Catfish instead for that purpose. Angry fanboys will rally from their mother's home basements to  attack me for saying this, but others should know enough to expect most people to question the sanity of favoring an extra application just to do a file search. But I'll just presume that there is a sane reason for this, which few people ever see, and I just haven't seen it yet. It's not really the culture of the Linux community to favor the running of more apps than are really necessary while spending more time between them in the process, am I right? If I am, then I need to know why, please!

---

### Post by rai4shu2 on 2012-05-20
Lumping everything together in one app is more the Microsoft philosophy, actually.

Have a look at this: [http://www.xfce.org/about](http://www.xfce.org/about)

> Xfce embodies the traditional UNIX philosophy of modularity and re-usability. It consists of a number of components that provide the full functionality one can expect of a modern desktop environment. They are packaged separately and you can pick among the available packages to create the optimal personal working environment.

The "Linux way" is to adhere to sensible standards and philosophies (among them is the UNIX philosophy, to which Xfce adheres). This is one of the main reasons I like it.

---

### Post by azertyh on 2012-05-20
hello,
i can search files in thunar and using catfish by right-clicking a folder. you haven't this feature?

---

### Post by Manmadegod on 2012-05-20
> **azertyh said:**
> hello,
i can search files in thunar and using catfish by right-clicking a folder. you haven't this feature?

Well, call me stooopid, but I wasn't aware of any file manager having that function in the right-click, and I suppose I just failed to notice. I just tried that in Nautilus, and it won't search this, but it's got the cool icon.   I just may become partial to having right-click functionality with applications which are in danger of becoming horribly cluttered with icons. So I found is the case with some of those KDE-based super file managers, which have icons for almost everything else.

---

### Post by Manmadegod on 2012-05-20
> **rai4shu2 said:**
> Lumping everything together in one app is more the Microsoft philosophy, actually.

Have a look at this: [http://www.xfce.org/about](http://www.xfce.org/about)



The &quot;Linux way&quot; is to adhere to sensible standards and philosophies (among them is the UNIX philosophy, to which Xfce adheres). This is one of the main reasons I like it.

  Lumping everything together in one REGISTRY is the Microsoft philosophy, and that's on security, not the user experience (where only fools deny they have been successful). Not that I haven't discovered power and efficiency at my fingertips which Microsoft would not be bothered with - on that there's plenty, but it does no good to eschew what has worked for Microsoft just to differentiate Linux from it.  

Sometimes too many features in one program can make it so bloated that it will trash older systems, and this may understandably be in conflict with  Xfce philosophy. I noticed while browsing file managers in the repos that some of the cluttered-looking KDE file managers are billed with catch-phrases such as "all the features you would expect and more".  

As I found out, Thunar (and maybe other file managers which I've tried) don't display a search icon, don't show it in the menu, but it's available in the right-click dialog - therefore, I no longer have this specific complaint with the Linux file-browsing experience.   

I was going to save other file-browsing issues for another post, but then you raised the philosophy.   

I don't think this one is Xfce-specific, when in fact only Xfce (I haven't tried KDE recently, so I don't know about that) even thought of those Microsoft information balloons which show vital file information. Bravo Xfce for adding that! That it is missing from Thunar, I expect Xfce to blame on the Thunar devs, but maybe you could shed some light on what is slowing down these and other devs. Microsoft has had this feature on its desktops AND it's file managers for the last 12 years! I find it to be indispensible at my job, where I have to use Windows XP. When you don't know the name of the file which you are looking for, but you have a good idea how big it is and you know the file extension, this cool popup saves you a lot of clicking just to see such data. You could change your view mode to display details as well, I know, but it tends to be a tedious chore setting it up to display that essential information instead of just so much useless information.   

Ditto on the click-to-rename feature on all Microsoft systems, which I have not found available anywhere in Linux-world. The world is squeezing every office with it's "go paperless" insanity, and this means a lot of new files need to be named and renamed. I get so frustrated not being able to do that so easily with the icon files I have created for my home Linux system! Why is this too much to ask of the Linux file manager devs?  

The philosophy you quoted is agreeable enough, but don't you think SOME interpretations of it may be getting in the way of development for a better user experience?  GNOME 3 is a really awful attempt at shifting developer focus to this, which should only be expected to insult those who are not computer-screen virgins. It kinda shows how out of touch some developers are with the end-user world which is still driven mostly by Microsoft and Apple.  Both of these companies owe their success to putting the end user first (and to hell with security, which I would never advocate), but if the above ideas which have for so long worked for Microsoft do not compromise user or system security, and do not significantly contribute to software bloating, then why not in Linux?

---

### Post by rai4shu2 on 2012-05-20
> **Manmadegod said:**
> ... I don't think this one is Xfce-specific, when in fact only Xfce (I haven't tried KDE recently, so I don't know about that) even thought of those Microsoft information balloons which show vital file information. Bravo Xfce for adding that! That it is missing from Thunar, I expect Xfce to blame on the Thunar devs, but maybe you could shed some light on what is slowing down these and other devs. Microsoft has had this feature on its desktops AND it's file managers for the last 12 years! I find it to be indispensible at my job, where I have to use Windows XP. When you don't know the name of the file which you are looking for, but you have a good idea how big it is and you know the file extension, this cool popup saves you a lot of clicking just to see such data. You could change your view mode to display details as well, I know, but it tends to be a tedious chore setting it up to display that essential information instead of just so much useless information.

Can't help you there. You're talking to a guy who uses Worker rather than Thunar for file managing. I like Worker because it embodies all the things I liked about Directory Opus 4 (before they went crazy and tried to make DO 5 too file managerish).

see: [http://www.boomerangsworld.de/worker/](http://www.boomerangsworld.de/worker/)
and: [https://bugs.launchpad.net/ubuntu/+source/worker/+bug/913077](https://bugs.launchpad.net/ubuntu/+source/worker/+bug/913077)

> Ditto on the click-to-rename feature on all Microsoft systems, which I have not found available anywhere in Linux-world. The world is squeezing every office with it's "go paperless" insanity, and this means a lot of new files need to be named and renamed. I get so frustrated not being able to do that so easily with the icon files I have created for my home Linux system! Why is this too much to ask of the Linux file manager devs?

If you have a lot of files to rename, Thunar is actually a very good option. Simply select all the files in the window and right-click (surprise!) and select rename. You then get a very nice multi-file rename tool for all those selected files.

> The philosophy you quoted is agreeable enough, but don't you think SOME interpretations of it may be getting in the way of development for a better user experience?...

Without a doubt. You know, people keep begging Xfce devs for a multiple tabs feature in Thunar. And even Worker has this feature, but Thunar will probably never get it. I think it's just as well. I'd rather see good, maintainable code that never goes too crazy than have feature bloat all more bugs than devs want to hear about.

---

### Post by Rodney9 on 2012-05-20
Thunar Wiki - 

[http://thunar.xfce.org/pwiki/documentation/start](http://thunar.xfce.org/pwiki/documentation/start)

Rodney

---

### Post by agillator on 2012-05-20
mmg: I suppose 'philosophy' is, like beauty, primarily in the eyes of the beholder. However, my experience with both Linux and Windows backs up the statement that Windows tends to expect software to do everything while Linux (Unix) expects software to do one thing but do it well. The Windows single registry approach is a specific design decision, not really a philosophy. 

In practice the philosophy of doing one thing well allows a user to use one command to do a string of things using pipes. I do that all the time either directly on the command line or by a script connecting those commands I wish to use. Perhaps because I have become so used to it I find I far prefer the Linux/Unix philosophy.

Your specific problem has obviously been answered by others, just thought I'd toss in my two cents worth on the philosophy thought.

---

### Post by HiImTye on 2012-05-20
you will find files much faster using the terminal
```
find $HOME/Videos -type f | grep MyMovie.avi
```

renaming is also pretty easy in the terminal
```
find $HOME/Videos -type f | grep -i .avi | rename -n 's|VideoSeries1|Series1|'
```
renames any file with the extension .avi inside the 'Videos' folder, or its' subfolders, replacing 'VideoSeries1' with 'Series1'
(but it doesn't write until you do it without the '-n')

---

### Post by Manmadegod on 2012-05-21
Thanks all for contributing, but now I'm afraid this is degenerating into another of those Philosophy of the Command-Line chest-pounding sessions which have always led to new users dumping Linux, and recently the excretion of that GNOME 3 turd by developers who don't study and don't care about their competition in the home PC market. 

That the command line works for you,  and that it will always work better than any GUI which can ever be developed is understood, but that argument is pointless. It doesn't work at all for most users, who don't have the luxury of time to study and learn volumes of syntax and technique. Without this the command line interface doesn't work at all, and that is why non-geek home users are not staying around. Linux forums are full of threads discussing which is the best distro the OP could set up for his sister or grandmother, but there's really no question on how any such mission ends! Perhaps some of you who look down your nose at all who don't use Terminal for e uverything may experience memory problems as you get older, may find that the system has changed to your frustration, and then you'll understand! 

The reason why the GUI is important, and should not be neglected (devs are encouraged to let it go when the command-line gurus talk like that) is that image learning is quicker and longer-lasting by factors of 10 for most people. People tend to view their computers as tools, not a way of life itself, and the latter is what they wish to avoid by approaching it through an environment which will not require years for them to master.  Maybe later they'll take up an interest in the greater power of the command line, (I know I would if I were more healthy),  but until then the basement geeks only stand to lose by chasing them away. More home users contribute to the development of more reliable software through more user feedback, and broader hardware compatibility.

On Windows experience, I have used all versions up through Windows 7, and I do agree with assessments of it here on versions after XP.  That XP is still favored after twelve years by large employers for their end users says that (security costs aside) that it has a pretty good shell for a GUI - there really isn't much that this one does without doing it well. What the Linux shells do better may counterbalance their failures to meet the standards which XP and Apple have set for freindly and intuitive. 

The additions being asked for are so minor for the differences they would make for recovering Windows users that it's beyond parochial pathos for the gurus to say it's asking one app to do too much!  This is where philosophy becomes doctrine, and with that there's always nonsense.

---

### Post by cortman on 2012-05-21
You know you can search for files in Thunar by just typing Ctrl+f and the name of the file?
Thunar has great search functions built in.
It was PcManFm that drove me nuts. Virtually zero search functionality, and using a separate app to search was very clunky for me. I wound up uninstalling it and installing Thunar on my LXDE Fedora OS. Works great.

---

