---
title: "HOW TO: Transparrent Terminal on the Desktop"
date: 2009-09-16
forum: General Help
---

### Post by M!SF!TS on 2009-09-16
Hello Everyone!

I am going to write a tutorial on how to Set a useful little tool on to your desktop, for ease of use, and to be pleasing to the Eye, After all... a boring Desktop Environment is... a boring Desktop Environment. make your Desktop nice, customize it, how YOU like and you will be happier, your computer could care-less, but Humans are Emotional beings and we DO care, so with that said lets make our box "Pretty"

This Tutorial is done in a "Picture Book" Format, Why ?... For ease of use, and because of the old saying goes, "A picture is worth 1,000 words" (actually I'm just lazy and hate to F@#%*&! type)

**[SIZE="5"]HOW TO: TRANSPARRENT TERMINAL 'EMBEDDED' ON YOUR DESKTOP![/SIZE]**
[IMG]http://i606.photobucket.com/albums/tt143/JacksonNicholasJ/Screenshot.png[/IMG]

When you are done it should look like this! (terminal in top left corner of screenshot)



**[SIZE="2"]STEP 1.[/SIZE]**
Open up a terminal:  Applications >> Accessories >> Terminal
[IMG]http://i606.photobucket.com/albums/tt143/JacksonNicholasJ/Screenshot-18.png[/IMG]




**[SIZE="2"]STEP 2.[/SIZE]**
Create a new Profile and name the profile: trans
[IMG]http://i606.photobucket.com/albums/tt143/JacksonNicholasJ/Screenshot-14.png[/IMG]

[IMG]http://i606.photobucket.com/albums/tt143/JacksonNicholasJ/Screenshot-1.png[/IMG]




**[SIZE="2"]STEP 3.[/SIZE]**
Edit the New Profile Preferences you just created
[IMG]http://i606.photobucket.com/albums/tt143/JacksonNicholasJ/Screenshot-15.png[/IMG]

UN-check the "Show Menu by default in new Terminals" Button
[IMG]http://i606.photobucket.com/albums/tt143/JacksonNicholasJ/Screenshot-2.png[/IMG]

Open the "Title and Command" tab and put in the "Initial Title" box: trans and change the Drop Menu to "Keep Initial Title"
[IMG]http://i606.photobucket.com/albums/tt143/JacksonNicholasJ/Screenshot-3.png[/IMG]

Change the colors to WHATEVER you want, but a good one to use for now is just check the box "Use colors from system theme"
[IMG]http://i606.photobucket.com/albums/tt143/JacksonNicholasJ/Screenshot-4.png[/IMG]

---

### Post by M!SF!TS on 2009-09-16
Please delete this reply if your a admin to ubuntu forums

---

### Post by M!SF!TS on 2009-09-16
Please delete this reply if your a admin to ubuntu forums

---

### Post by M!SF!TS on 2009-09-16
Next you need to change the background Transparency, so click on the option that says "Transparent Background" and set the scroll bar to "None"
[IMG]http://i606.photobucket.com/albums/tt143/JacksonNicholasJ/Screenshot-5.png[/IMG]


Now Disable the Scrollbar, to do that click on the "Scrolling" tab and click the drop down menu and select "Disable" (you can even set the amount of lines you want to be able to scroll back (nice option if you like looking at past CLI inputs like myself)
[IMG]http://i606.photobucket.com/albums/tt143/JacksonNicholasJ/Screenshot-6.png[/IMG]

[SIZE="4"]**Step 4.**[/SIZE]

Now open up Compizconfig Settings Manager
[IMG]http://i606.photobucket.com/albums/tt143/JacksonNicholasJ/Screenshot-19.png[/IMG]

Make sure Regex is enabled, (type in the search bar "rege" and it will pop right up, so you dont have to search for it if you like)
[IMG]http://i606.photobucket.com/albums/tt143/JacksonNicholasJ/Screenshot-7.png[/IMG]

Then goto the "Place Window" option and enable it if it is not and open it up
[IMG]http://i606.photobucket.com/albums/tt143/JacksonNicholasJ/Screenshot-8.png[/IMG]

Once the "place Window" option is open, click on the "Fixed Position" Tab and set it to the setting you like, (Hint: 0 x 0 like on the picture is the very top left of your monitor)
[IMG]http://i606.photobucket.com/albums/tt143/JacksonNicholasJ/Screenshot-9.png[/IMG]

now go back to the main interface of compizconfig application and goto the "Windows Rules" option ensure it is enabled and then click on it
[IMG]http://i606.photobucket.com/albums/tt143/JacksonNicholasJ/Screenshot-10.png[/IMG]

Now under the "Matches" Tab, add      title=trans      to the following Boxes you see in this screenshot
[IMG]http://i606.photobucket.com/albums/tt143/JacksonNicholasJ/Screenshot-11.png[/IMG]

---

### Post by M!SF!TS on 2009-09-16
Now once you have all those settings filled click on the next tab "Size Rules" and add the settings you wish, this option will let you pick how BIG you want the transparent background of the terminal, i recommend you pick enough space to work on in the terminal you don't want it to small, and you don't want it to take up you whole desktop (well you can if you wish it is transparent...) if you are unsure use my settings, and change them gradually as you see fit
[IMG]http://i606.photobucket.com/albums/tt143/JacksonNicholasJ/Screenshot-12.png[/IMG]

Now your almost done. here is the last step...

[SIZE="4"]**Step 4.**[/SIZE]


Setting the transparent terminal to default.
Goto "Edit" in toolbar menu, and select the option "Profile Preferences"
[IMG]http://i606.photobucket.com/albums/tt143/JacksonNicholasJ/Screenshot-15.png[/IMG]

Now find the small drop down menu just above the "Close" button, and select the new terminal Profile "trans" and that's it... close the current terminal your working in, and reopen the terminal it should appear as if to be a transparent terminal looking all nice and clean on your desktop, now would also be a good time to go back threw and change any color or size option that may fit you best if you followed my terminal as a default
[IMG]http://i606.photobucket.com/albums/tt143/JacksonNicholasJ/Screenshot-16.png[/IMG]






Now if you want to add it to your start up applications and you use the Startup Applications program under   System >> Preferences >> Startup Applications           add a new starup with this being the code to execute

gnome-terminal --window

now if you use a start-up_script, just simple add the same like of code to you start-up_script

gnome-terminal --window &



This concludes the tutorial on how to make a transparent terminal on your desktop, its fun easy and makes the terminal look more friendly in my opinion.. enjoy and I hope this helps some people in their quest to understand Linux and the Gnome Desktop Environment better

-Nick

---

### Post by M!SF!TS on 2009-09-16
I screwed up, could a admin move this to the "Tutorial's and Tips" discussion

---

### Post by Dr. Oddbio on 2009-11-15
I followed all of your instructions and it looks great, however I still have the window border and title bar show up. It doesn't look like it should be there though from your screenshot.
But other than that, great tutorial, the pictures are helpful.

---

### Post by koshari on 2009-11-18
> **Dr. Oddbio said:**
> I followed all of your instructions and it looks great, however I still have the window border and title bar show up. It doesn't look like it should be there though from your screenshot.
But other than that, great tutorial, the pictures are helpful.

window decoration not present here until i added ```
!(title=trans)
``` to compiz setings > window decoration > decoration windows

i also suggest the themed terminal gets launched with 
```

gnome-terminal --window-with-profile=trans
``` so you can keep the default prifile being launched in the default fashion.

also its prolly a good idea to have the x offset at least 150px as most automounted launchers/screenprints are in placed the left part of the screen.

but all in all nice tut.

---

### Post by WrinkledCheese on 2010-04-24
I would like an update to this tutorial.  It's very awesome.  I got the window to appear at boot, but I think that's just as a startup application becuase I can't get the window to stay put.  I think it might be due to the final task in step 4 requiring the image to be available.

> 
Now under the "Matches" Tab, add      title=trans      to the following Boxes you see in this screenshot


The screenshots are no longer available on photobucket anymore, which means this tutorial is lacking what I think is very important information.  I'm going to see if I can figure it out on my own and publish the update on this thread.  If I cannot then someone else will have to update this thread.

---

### Post by Rocket J Squirrel on 2010-04-24
Aw phooey. I got midway through the tutorial before I discovered that it uses compiz. I don't have compiz installed, wasn't planning to install compiz. But now my terminals launch with a transparent background, which doesn't work for me. I'd to go back to the default profile, but the menu is gone because I followed this step:

UN-check the "Show Menu by default in new Terminals" Button

How can I get the menu back so I can go back to the default profile?

---

