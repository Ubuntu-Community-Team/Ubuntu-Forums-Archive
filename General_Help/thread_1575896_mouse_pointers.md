---
title: "mouse pointers"
date: 2010-09-16
forum: General Help
---

### Post by hotshot247 on 2010-09-16
when i change my mouse pointer, why does it only change into what i want when im in a window, like viewing files or in firefox or something like that? when i'm on the taskbar, on the desktop, or on the ubuntu menu, it switches to the default one. how can i make it stay the pointer that i want all the time?

---

### Post by hotshot247 on 2010-09-17
i found out that when i turn the visual effects really high, the mouse stays the default mouse pointer until i am in a window like browsing with firefox or something like that but i can turn the visual effects down and the pointer stays the way i want it all the time. i like the visual effects so is their a way to keep the mouse pointer the way i want it and keep the visual effects? their has to be a way.

---

### Post by WorMzy on 2010-09-17
There is a way, but it's a bit of a hack.

You need to create a text file at ~/.icons/default, call it "index.theme" and put the following content inside it:

```
[Icon Theme]
Name = OxyTheme
Comment = None
Example = Yes
Inherits = [COLOR="Red"]Oxygen_Obsidian[/COLOR]
```

The part in red is all you need to change, it should be the name of the icon theme that you want to use. The name should be written exactly the same way as it appears in the cursor list. You can change the other variables if you want, they don't make any difference though.

The change may not take effect until you log out and back in, but once it works, you can keep visual effects and your preferred mouse cursor.

---

### Post by hotshot247 on 2010-09-17
cool. i just tried it and it works. thanks a lot! this has been getting on my nerves for a couple of days. lol

---

### Post by rs87424 on 2010-09-26
> **WorMzy said:**
> There is a way, but it's a bit of a hack.

You need to create a text file at ~/.icons/default, call it "index.theme" and put the following content inside it:

```
[Icon Theme]
Name = OxyTheme
Comment = None
Example = Yes
Inherits = [COLOR="Red"]Oxygen_Obsidian[/COLOR]
```

The part in red is all you need to change, it should be the name of the icon theme that you want to use. The name should be written exactly the same way as it appears in the cursor list. You can change the other variables if you want, they don't make any difference though.

The change may not take effect until you log out and back in, but once it works, you can keep visual effects and your preferred mouse cursor.
how do you go to .icons?  home folder?  and when I make this text file will it interfere with something else because every time I make a new text file something else has to be fixed

---

### Post by Ultra_Man on 2010-09-26
> **rs87424 said:**
> how do you go to .icons?  home folder?  and when I make this text file will it interfere with something else because every time I make a new text file something else has to be fixed

ctrl + h in the home folder to view hidden files. 

And all you have to do is log out and log back in for the mouse theme change to completely take effect. At least, on my ubuntu.

---

### Post by WorMzy on 2010-09-26
Yes, Ctrl+H will allow you to see the folder; or you can press Ctrl+L and type it in to the address bar.

It doesn't conflict with anything, it merely overrides the system defaults for your user.

---

### Post by rs87424 on 2010-09-26
I went through the whole process and it doesn't work with mine... I had to change the appearance setting to having no effects

---

### Post by rs87424 on 2010-09-26
I put into the text file "handhelds" which is the name of the pointer I want for the mouse, it seems to not work for my ubuntu lucid

---

### Post by WorMzy on 2010-09-26
The text file has to be called "default". Copy and paste the code I wrote before and change the "Inherits = Oxygen_Obsidian" line to "Inherits = handhelds".

---

### Post by rs87424 on 2010-09-27
I changed the name of the file to default and put in the desired name of the cursor and for some reason there is no change... I am not sure what is happening to be honest but I have been dealing with the mouse problem for a while now which resulted after an update

ps: I also restarted the computer as well

---

### Post by WorMzy on 2010-09-27
Oops. I made a mistake in my last post. The file should be called "index.theme", and it should be inside a *folder* called "default", which should be inside your "~/.icons" folder.

This command will create the file for you with the right content.

```
mkdir -p ~/.icons/default && echo '[Icon Theme]\nName = OxyTheme\nComment = None\nExample = Yes\nInherits = handhelds' > ~/.icons/default/index.theme
```

Copy and paste that into a terminal.

If that doesn't fix the problem, then I guess it really doesn't work on your computer.

---

### Post by rs87424 on 2010-09-27
> **WorMzy said:**
> Oops. I made a mistake in my last post. The file should be called "index.theme", and it should be inside a *folder* called "default", which should be inside your "~/.icons" folder.

This command will create the file for you with the right content.

```
mkdir -p ~/.icons/default && echo '[Icon Theme]\nName = OxyTheme\nComment = None\nExample = Yes\nInherits = handhelds' > ~/.icons/default/index.theme
```

Copy and paste that into a terminal.

If that doesn't fix the problem, then I guess it really doesn't work on your computer.
yeah for some reason its not working... would it be because maybe the code is for icon themes and not for cursor themes?  or are they both related in this code?

---

### Post by WorMzy on 2010-09-27
It's in the icon folder, and it's declaring an icon theme, but it only affects the cursor. No idea why. It's worked for everyone else in this topic, so I'm not sure why it's not working for you. You'll have to wait for someone else to post a different solution, because that's the only one I know. Sorry.

---

### Post by rs87424 on 2010-09-28
well here is the thing.. I did change the settings once to make all of my windows to have the close and minimize boxes on the left side instead of the right side and my cursor was working fine for a while until one update happened and everything has been acting strange including the cursor.  sometimes my panels won't even show up at startup and I have to restart my computer just to make them come up again... its really frustrating

---

### Post by rs87424 on 2010-09-28
I wonder if this might have something to do with Metacity?  I am not sure how to check if thats causing the problems...

---

### Post by rs87424 on 2010-10-03
I have tried everything I could think of and it still shows the same default pointer but only displays the desired pointer when looking at a hyperlink... I think its a bug to be honest

---

