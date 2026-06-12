---
title: "Recording in recordMDesktop is just weird"
date: 2011-03-17
forum: General Help
---

### Post by WlaadDyaab on 2011-03-17
Hi

I've almost sorted out all my problems with recordMyDesktop but there's bugs that need fixing

I viewed the video after I stopped the recording, here's a screen shot from the recorded video:

[ATTACH]186382[/ATTACH]

[ATTACH]186383[/ATTACH]

It's just horrible :(

I searched for the Terminal command to update and upgrade my Linux system: [http://ubuntuforums.org/showthread.php?t=1128960](http://ubuntuforums.org/showthread.php?t=1128960)

I tried these two commands in Terminal:

> sudo apt-get update && sudo apt-get upgrade

And

> sudo apt-get upgrade && sudo apt-get update

But the problem is still there. Is this a known bug that can be fixed or is it something else?

Thanks

---

### Post by Rasa1111 on 2011-03-17
Ive never gotten "recordmydesktop" to record perfectly.
 There has always been one issue or another with it. 

However,
 Ive recently been using an app/program called "Kazam" , and it works amazingly well!

Perfect resolution, speed, clarity...
It just works soo nicely. 

Maybe check that out?

[http://www.webupd8.org/2010/09/try-kazam-new-screencasting-application.html](http://www.webupd8.org/2010/09/try-kazam-new-screencasting-application.html)

---

### Post by pqwoerituytrueiwoq on 2011-03-17
i have had the same issue with that app (recordmydesktop) turn compiz off
xvidcap works with compiz

---

### Post by supershin on 2011-03-17
Kazam is new to scene without much features though.

---

### Post by WlaadDyaab on 2011-03-17
> **Rasa1111 said:**
> Ive never gotten "recordmydesktop" to record perfectly.
 There has always been one issue or another with it. 

However,
 Ive recently been using an app/program called "Kazam" , and it works amazingly well!

Perfect resolution, speed, clarity...
It just works soo nicely. 

Maybe check that out?

[http://www.webupd8.org/2010/09/try-kazam-new-screencasting-application.html](http://www.webupd8.org/2010/09/try-kazam-new-screencasting-application.html)

Rasa1111 you just made my day!

I simply can't describe how siiiiimple it is to use. Kazam is great!

Thank you so much

Now to make other people benefit:-

Downloading Kazam:

- [http://www.omgubuntu.co.uk/2010/09/kazam-0-1-available-the-screencasting-bar-on-linux-just-got-raised/](http://www.omgubuntu.co.uk/2010/09/kazam-0-1-available-the-screencasting-bar-on-linux-just-got-raised/)
- Copy-paste this into Terminal:

To get to Terminal: Applications > Accessories > Terminal (short-cut: ctrl + alt + T)

> ***sudo apt-get install kazam***

- Press "Enter" (or "return key")
- It's going to stop so press "y" letter on your keyboard
- "Return key"
- After it finishes downloading: Applications > Sound & Video > Kazam Screencaster

Done!

To use Kazam:

Applications > Sound & Video > Kazam Screencaster

- In "Kazam Screencaster" box, press "Record"
- Simply click anywhere or do anything for a couple of seconds
- To stop the recording:

[ATTACH]186391[/ATTACH]

You'll find this icon in the top-right corner of your Desktop

- Left-click on it > Finish Recording
- In the "Kazam Screencaster" box just tick "Save for later use..." > Continue
- In the "Save screencast" box click on "Save" (this is an optional repository, you can choose "Desktop" if you want, or whatever repository that suits you. But I'll go with the default "Videos" repository for now)

- To play your video that you just recorded: Places > Videos

Then you should find your recorded video of your Desktop :)

You can then upload tutorials (or whatever you fancy) on YouTube for example

When you watch tutorials on YouTube you normally see that they're zooming in and out to show their actions i.e. what they click on, what they view, how they change this option and how they change that...etc

This is a feature from a program called Compiz Fusion

And the feature is called "Enhanced Zoom Desktop"

(If you're interested, read the following please)

To download Compiz Fusion there's two ways, but I'll start with the easiest:

- Applications > Ubuntu Software Centre
- In "Ubuntu Software Centre" box, type or copy/pase "compiz fusion" > Install

- To open Compiz Fusion: Applications > System Tools > Compiz Fusion Icon
- On the top-right corner of the screen right-click on the icon > Settings Manager

- In the "CompizConfig Settings Manager" box > tick "Enhanced Zoom Desktop

In the  nameless box that pops up either keep choosing "Ignore Conflicts" or "Resolve Conflicts"

- I normally choose "Resolve Conflicts" > Set Zoom Box anyway > Set Zoom In anyway

That normally works fine for me

To test the Zoom in feature:

- In the "CompizConfig Settings Manager" box > choose "Enhanced Zoom Desktop" (don't un-tick it)

Notice how the "Zoom In"< "Zoom Out", "Zoom Box", notice how all of them have this being mentioned along their lines; "<Super>Button..."

To be honest I have no idea what "Button4", "Button5", and what "Button2" are, but I know that "<Super>" is the Microsoft key on our keyboards

Now minimize everything. Or leave it as it is, there's no difference

To use the Zoom in and out feature:

- Hold <Super> key (Microsoft's logo key) > Use your mouse for scrolling in and out :)

Done :)

There are things that I haven't mentioned:

- In the instructions I never mentioned that I opened Kazam and ticked the "Record Audio from:". That's because I don't need to use that option, but you're free to do so

- I also never mentioned the second way to download Compiz Fusion. If for some reason you still can't get Compiz Fusion then here's the link to how to download it through Terminal: [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

And if there are still problems just drop in a reply or a post and either I, or one of the good people - who are more experienced than me - in this forum would reply back to you :)

---

### Post by WlaadDyaab on 2011-03-17
> **supershin said:**
> Kazam is new to scene without much features though.

Oh noo, if simplicity means a "good working program" then that's better

If more features are needed to get better results and is functioning very well then that's all there is to it

But recordMyDesktop really gave me headache when all I did was that I tried my best to stick to the tutorials...etc

Anyway, these programs are open source and most of them are projects that have been done by pure experienced people that are loyal to the meaning of doing things for the sake of knowledge and sharing useful stuff. It's from their precious time too

So I still have positive intentions for recordMyDesktop Lol, and will try to be like them in terms of using my time to help others as much as my limit allows me too

---

### Post by Rasa1111 on 2011-03-17
> **WlaadDyaab said:**
> Rasa1111 you just made my day!

I simply can't describe how siiiiimple it is to use. Kazam is great!

Thank you so much



Hi mate,
you're welcome!
glad it helped! :D <3

---

