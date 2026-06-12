---
title: "How do you manage your home folder?"
date: 2010-03-15
forum: General Help
---

### Post by nschubach on 2010-03-15
I was digging through my laptop tonight and I realized I'd like more control over my home folder.  It seems as though programs installed on my laptop just pick their own conventions for saving data and none of them are the same.  Some programs store their data in self named hidden folders, others use ~/.config and others use ~/.local/share to put their stuff.

Is there a way I'm missing to get all these to cooperate or are we doomed to always having programs making themselves at "home" and just tossing off their shoes wherever they like?

---

### Post by IllegalCharacter on 2010-03-15
I'm guessing it depends on the program, but chances are you're just going to have to live with them doing whatever they feel like in your home folder. Fortunately the folders are usually hidden, so you don't see them during normal usage of your computer. Are the folders causing a problem?

---

### Post by nschubach on 2010-03-15
That depends on what you mean by problem.  ;)

Cluttering up my folders, even if they're hidden is a little disheartening.

---

### Post by km0r3 on 2010-03-15
> **nschubach said:**
> I was digging through my laptop tonight and I realized I'd like more control over my home folder.  It seems as though programs installed on my laptop just pick their own conventions for saving data and none of them are the same.  Some programs store their data in self named hidden folders, others use ~/.config and others use ~/.local/share to put their stuff.

Is there a way I'm missing to get all these to cooperate or are we doomed to always having programs making themselves at "home" and just tossing off their shoes wherever they like?

In Windows a program usually stores information in the Registry or in RC files.

In Linux there's nothing like that (gconf?), instead information gets saved in those "hidden" folders. Personally I think this is more convenient than other ways.

---

### Post by asmoore82 on 2010-03-15
[quote=nschubach]**How do you manage your home folder?**[/quote]

\\:D/ Don't Worry. Be Happy! \\:D/

That's what a home folder is for.

I can't stand that Windows XP gives a shortcut to "My Documents" instead of the Home folder.
At least with Vista and 7 they finally copied the right way to do it.

---

### Post by ndefontenay on 2010-03-15
Yeah. I don't mind about the hidden folders. I just liek the idea that they are there when I need them. Ignoring is good enough!

Otherwise, I create an extra work folder which usually stores any kind of work I got to do. my wife and daughters have a folder with their name on it.

They are not really into having their own username and folders...

Nico

---

### Post by brian mcgee on 2010-03-15
Meh, hidden folders never bothered me. ;)

---

### Post by dcstar on 2010-03-15
> **nschubach said:**
> I was digging through my laptop tonight and I realized I'd like more control over my home folder.  It seems as though programs installed on my laptop just pick their own conventions for saving data and none of them are the same.  Some programs store their data in self named hidden folders, others use ~/.config and others use ~/.local/share to put their stuff.

Is there a way I'm missing to get all these to cooperate or are we doomed to always having programs making themselves at "home" and just tossing off their shoes wherever they like?

User based configuration goes into each user's /Home folder because each user can have things set up the way each user likes - as it should be.

System based configuration stays well out of any user folders and goes into the Linux system folders - as it should be.

Let the people who have taken a lot of time and effort to set these things up to work correctly have some credit for knowing what they are doing, because as a lot of posts in these forums prove some people who believe that they know better don't.

---

### Post by nschubach on 2010-03-16
> **dcstar said:**
> User based configuration goes into each user's /Home folder because each user can have things set up the way each user likes - as it should be.

System based configuration stays well out of any user folders and goes into the Linux system folders - as it should be.

Let the people who have taken a lot of time and effort to set these things up to work correctly have some credit for knowing what they are doing, because as a lot of posts in these forums prove some people who believe that they know better don't.

I understand that... and I understand that it's a good thing.  I just wish there was a way for me to enforce rules on where they put that stuff within my home folder.  For instance, I'd want to put all configuration files under ~/.config/appname instead of whatever the programmer decided when they compiled the application.  I like a clean and organized file structure like I like living in a clean and organized home.  To me, it's like buying a couch and having the furniture store glue the instruction book on the wall of my kitchen.

---

### Post by dcstar on 2010-03-17
> **nschubach said:**
> I understand that... and I understand that it's a good thing.  I just wish there was a way for me to enforce rules on where they put that stuff within my home folder.  For instance, I'd want to put all configuration files under ~/.config/appname instead of whatever the programmer decided when they compiled the application.  I like a clean and organized file structure like I like living in a clean and organized home.  To me, it's like buying a couch and having the furniture store glue the instruction book on the wall of my kitchen.

You are free to download the source code for any app and recompile them to do whatever you want.

---

