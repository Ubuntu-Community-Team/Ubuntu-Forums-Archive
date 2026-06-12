---
title: "[Lubuntu] How to hide desktop icons, and other questions."
date: 2011-11-04
forum: General Help
---

### Post by Finitemight on 2011-11-04
[FONT=Courier New]Hey all!,
 
I just recently switched from Windows Vista to Ubuntu. Then I switched from Ubuntu to Lubuntu! I decided to partition my drive so I could have BOTH windows and Lubuntu.... And I gotta say I am loving Lubuntu. It is what Ubuntu was prior to all this latest graphical enhancement slowing stuff...
 
But I digress. To the topic at hand...
 
1) I want to know how to hide desktop icons. In ubuntu, all I had to do was hit "Alt+F2" and hit up the "gconf-editor", but that does not work for lubuntu (guessing because it is not gnome). 
[/FONT]
[FONT=Courier New]
[/FONT]
[FONT=Courier New]2)keybinding shortcuts has been a big issue with me here. Normally, for ubuntu you just go to "system" and hit the keyboard shortcuts to customize what you want to. It would have a fairly large list, and you just scrolled through and clicked the command you wanted. After that, you simply touched the keys you would want the shortcut to actually be (instead of what it is) and that was it! I have no idea how to access that (if it is even available) for lubuntu.[/FONT]


[FONT=Courier New]Those two are the big gripes that I have. I heard anything could be solved in lubuntu on the forums... Please help!:D
[/FONT]
[FONT=Courier New]
[/FONT]

[FONT=Courier New]
[/FONT] 
 [FONT=Courier New]
[/FONT]

---

### Post by SteveDee on 2011-11-04
> **Finitemight said:**
> ...2)keybinding shortcuts...

I haven't come across a GUI to edit keyboard shortcuts.

They are configured in the XML file "lubuntu-rc.xml" and you can pull out a jumbled list by going to a terminal and typing:-
```

grep -A 2 "<keybind" ~/.config/openbox/lubuntu-rc.xml

```

As for Q1...sorry I don't understand the question.

---

### Post by Finitemight on 2011-11-04
Thanks for that response, but I am looking for a GUI solution if possible. 

What I meant by the first question is that I managed to hide the desptop icons as they have done in this post

[http://www.junauza.com/2010/06/how-to-hide-desktop-icons-in-ubuntu.html](http://www.junauza.com/2010/06/how-to-hide-desktop-icons-in-ubuntu.html)

These suggestions posited do not work for lubuntu, only ubuntu.

Thanks in advance community!

---

### Post by amjjawad on 2011-11-04
> **Finitemight said:**
> Thanks for that response, but I am looking for a GUI solution if possible. 

What I meant by the first question is that I managed to hide the desptop icons as they have done in this post

[http://www.junauza.com/2010/06/how-to-hide-desktop-icons-in-ubuntu.html](http://www.junauza.com/2010/06/how-to-hide-desktop-icons-in-ubuntu.html)

These suggestions posited do not work for lubuntu, only ubuntu.

Thanks in advance community!

Hello and Welcome to Ubuntu Forum and ... Hello and Welcome to Lubuntu World :D

I'm a member of Lubuntu Team and I'd like to thank you for using Lubuntu. Such a great OS, isn't it?

As for your first question regarding a GUI application to edit the Shortcuts, I don't know of any but what is wrong with the manual way? :P

As for the second questions, there are two approaches:

1- By Default, there is NO icons on Lubuntu Desktop. You can place them somewhere else.

2- If my first point is invalid and doesn't make sense, ignore it and do one simple thing: Rename any file and just put "." at the very beginning then press OK. That is all :)

Have a look at my signature, there is One Stop Thread that wroth to be checked ;)

---

### Post by Finitemight on 2011-11-04
Wow that is an incredible amount of infomration, and thanks for compiling it all together. This is crazy... everyone seems to be helping out of the willingness to do so!

I wanted a default GUI because ubuntu already has one. i thought it would be easy for it to carry over. Lubuntu has no icons, but when you transfer folders onto the desktop, you see them prominently displayed on the desktop wallpaper.

I tried that adding the period to the end, but alas to no avail.
I will read through, and hopefully there is a gui fix to this problem. It is such a small thing, but noticeable when it is not there.

thanks for the suggestions and i will try them out... though the whole "programming yourself" thing seems a bit daunting... (being a newb)

I mean the whole reason we have GUI interface in the first place is to get away from the average user having to "sudo" there way to doing something. It is counter intuitive and counter productive to any OS period.

---

### Post by amjjawad on 2011-11-04
> **Finitemight said:**
> Wow that is an incredible amount of infomration, and thanks for compiling it all together. This is crazy... everyone seems to be helping out of the willingness to do so!
When of the things I enjoy is to help people and that amount of information, no matter how hard/easy to put them together, is really nothing compared to how helpful it will be to any user. I'm here to make sure each and every Lubuntu User get his/her fair share of help and support :)
Thank you for your nice words!


> I wanted a default GUI because ubuntu already has one. i thought it would be easy for it to carry over. 

I see your point but Lubuntu is NOT Ubuntu :)

> Lubuntu has no icons, but when you transfer folders onto the desktop, you see them prominently displayed on the desktop wallpaper.

You mean when you place a folder on the Desktop?

> I tried that adding the period to the end, but alas to no avail.

You didn't read my post carefully. I mentioned at the very beginning NOT the end. The Screenshot show it all, I guess :)

> I will read through, and hopefully there is a gui fix to this problem. It is such a small thing, but noticeable when it is not there.
If you are referring to Hiding icons then that's really useless as long as you can do it with one small "." :)


> thanks for the suggestions and i will try them out... though the whole "programming yourself" thing seems a bit daunting... (being a newb)

Humans always underestimate their real ability of learning. Unleash these abilities and you'll see how far you can go ;)


> I mean the whole reason we have GUI interface in the first place is to get away from the average user having to "sudo" there way to doing something. It is counter intuitive and counter productive to any OS period.

Same thing I was searching for when I first started with Linux. I was avoid the Terminal but now, I can't use anything but the Terminal. Terminal is so much easy once you learn how to deal with it. Trust me in this :)

Let me know if you need anything else ;)

---

### Post by Finitemight on 2011-11-05
> **amjjawad said:**
> When of the things I enjoy is to help people and that amount of information, no matter how hard/easy to put them together, is really nothing compared to how helpful it will be to any user. I'm here to make sure each and every Lubuntu User get his/her fair share of help and support :)
Thank you for your nice words!



I see your point but Lubuntu is NOT Ubuntu :)


You mean when you place a folder on the Desktop?


You didn't read my post carefully. I mentioned at the very beginning NOT the end. The Screenshot show it all, I guess :)


If you are referring to Hiding icons then that's really useless as long as you can do it with one small "." :)



Humans always underestimate their real ability of learning. Unleash these abilities and you'll see how far you can go ;)




Same thing I was searching for when I first started with Linux. I was avoid the Terminal but now, I can't use anything but the Terminal. Terminal is so much easy once you learn how to deal with it. Trust me in this :)

Let me know if you need anything else ;)

I put a period at the beginning and that did not work. I put a period at the end, and that did not work either. Neither worked is what i meant to edit in there.

I guess I will read into this further, but in order for this distro to proliferate there needs to be ease of access (as with any operating system). terminal commands are not easy to adopt, and will turn most people off. Still I will try though

thanks

---

### Post by amjjawad on 2011-11-05
> **Finitemight said:**
> I put a period at the beginning and that did not work. I put a period at the end, and that did not work either. Neither worked is what i meant to edit in there.

I guess I will read into this further, but in order for this distro to proliferate there needs to be ease of access (as with any operating system). terminal commands are not easy to adopt, and will turn most people off. Still I will try though

thanks

What release of Lubuntu are you using? 11.04 here and it does work for me.

I agree, specially for new users coming from Windows or even Ubuntu where most of the stuff can be done via GUI. But again, from experience, it looks hard but appearances could be deceiving :)

---

### Post by Finitemight on 2011-11-05
> **amjjawad said:**
> What release of Lubuntu are you using? 11.04 here and it does work for me.

I agree, specially for new users coming from Windows or even Ubuntu where most of the stuff can be done via GUI. But again, from experience, it looks hard but appearances could be deceiving :)

I am using the latest version of Lubuntu (11.10).

---

### Post by SteveDee on 2011-11-05
> **Finitemight said:**
> ...I wanted a default GUI because ubuntu already has one.....

The reason there are so many Debian/Ubuntu distros is because everyone has their own idea of what is required. I use Lubuntu because its light, fast and runs on my collection of old computers. If it used Gnome and did what Ubuntu can do, I'd probably have to look for another distro...and maybe have to switch to ....(Gulp!) ...Puppy Linux!

So it could be that Lubuntu is not for you. However, there may be other ways of working that could get around your problem. For example, if you don't want passers-by to see the titles of your desktop files, why not put a folder on the Desktop called "junk" and put your files in there.

Alternatively, the file manager on Lubuntu is quite friendly, so its easy to add a folder and bookmark it, so it appears in the left-pane and is quick to get to.

I hate clutter anyway, and think the only thing that should be on my Desktop is a cup of coffee!

I hope this is food for thought.

---

### Post by amjjawad on 2011-11-05
> **Finitemight said:**
> I am using the latest version of Lubuntu (11.10).

I just tested on Lubuntu 11.10 and it does work. When you put "." at the very beginning of any file/folder, it  does fade away from the Desktop even though you set PCManFM to show Hidden Files.

There must be something wrong. Have you installed something or replaced something is already installed? is this fresh new installation? 

The "." approach can be used on Ubuntu as well. I see no point of using a program while you can do it manually. Just my personal opinion :)

---

### Post by Finitemight on 2011-11-05
> **amjjawad said:**
> I just tested on Lubuntu 11.10 and it does work. When you put "." at the very beginning of any file/folder, it  does fade away from the Desktop even though you set PCManFM to show Hidden Files.

There must be something wrong. Have you installed something or replaced something is already installed? is this fresh new installation? 

The "." approach can be used on Ubuntu as well. I see no point of using a program while you can do it manually. Just my personal opinion :)


wow. you know what i did? I right clicked on the folder (which opened up file properties) and then i inserted a "." there. I did not right click and hit rename and then put a "."

heh.

thanks! That is one way of doing it.

---

The way I wanted to hide the desktop icons was the way it was done in gnome. by going to "gconfig-editor" then [B]apps > nautilus > desktop  
and then hiding the icons that way. Then I wanted to put a shortcut to the desktop and attach it to the quick launch toolbar (another thing I cannot seem to edit as easily as i could in ubuntu, gui wise***) ***so that it was immediatly not visible, but still one click away (as opposed to putting a "." in front, and then going to the option to show all hidden files and folders).

 I hope what I typed made sense. Thank you for the quick response and the alternate way of doing this!

lol. lubuntu. Think Different.
[/B]

---

### Post by amjjawad on 2011-11-05
> **Finitemight said:**
> wow. you know what i did? I right clicked on the folder (which opened up file properties) and then i inserted a "." there. I did not right click and hit rename and then put a "."

heh.

thanks! That is one way of doing it.


I truly don't know why you can't do that with Rename? anyway, I'm glad you figured it out your way :) that's the most interesting part about Linux when you can do something in too many different ways :)

> The way I wanted to hide the desktop icons was the way it was done in gnome. by going to "gconfig-editor" then [B]apps > nautilus > desktop  
and then hiding the icons that way. Then I wanted to put a shortcut to the desktop and attach it to the quick launch toolbar (another thing I cannot seem to edit as easily as i could in ubuntu, gui wise***) ***so that it was immediatly not visible, but still one click away (as opposed to putting a "." in front, and then going to the option to show all hidden files and folders).

 I hope what I typed made sense. Thank you for the quick response and the alternate way of doing this!
[/B]
Yes, that does make sense from the very beginning but yet again, if one approach/way/method works on one OS, it doesn't mean it will work too on the other. Having too different ways is what keep Linux interesting and fun. Why there are more than 300 Active Linux Distributions and other 300 are on the waiting list on Distrowatch? there must be a good reason for that :)
If Linux wasn't flexible enough, that could never happened.

> 
[B] lol. lubuntu. Think Different.
[/B]
Yes, exactly and that's not only about Lubuntu but Linux in General :)

My approach is: [KISS]("http://en.wikipedia.org/wiki/KISS_principle")

SliTaz is adopting that approach.
[http://www.slitaz.org/en/devel/forge.php](http://www.slitaz.org/en/devel/forge.php)

---

