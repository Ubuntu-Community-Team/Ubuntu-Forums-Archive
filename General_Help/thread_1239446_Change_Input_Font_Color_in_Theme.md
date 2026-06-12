---
title: "Change Input Font Color in Theme"
date: 2009-08-13
forum: General Help
---

### Post by CrusaderAD on 2009-08-13
Is there a way to find and change the input fore color (font color) using certain themes? I really like the "Darker" Themes but the input fields on web forms have a black background and a dark grey font which can barely be seen.

---

### Post by stinkeye on 2009-08-13
> **raptormanad said:**
> Is there a way to find and change the input fore color (font color) using certain themes? I really like the "Darker" Themes but the input fields on web forms have a black background and a dark grey font which can barely be seen.
gnome-color-chooser

---

### Post by CrusaderAD on 2009-08-13
> **stinkeye said:**
> gnome-color-chooser

This seems like a cool tool, thanks, but it lists a bunch of colors that aren't used by the system. Reds and greens and weird colors. I opened the Theme Default profile and it has the same thing. How do you work this thing?

---

### Post by stinkeye on 2009-08-13
> **raptormanad said:**
> This seems like a cool tool, thanks, but it lists a bunch of colors that aren't used by the system. Reds and greens and weird colors. I opened the Theme Default profile and it has the same thing. How do you work this thing?

Not sure what you mean but if you click on the color boxes you can choose a color.
You have to tick the box first.
I just do a bit of trial and error and if I don't like it click on the revert button which will take you back to the theme default.
Once You've got your colors sorted goto file-save as, and save as < whatever > .gnomecc.
Then when trying new themes you can revert the colors or if you go back to your original dark theme you just load your .gnomecc file.

---

### Post by CrusaderAD on 2009-08-13
I would attached a screenshot, but the thread won't let me even select the option to do so.

---

### Post by oldos2er on 2009-08-13
Open the Appearance app (System, Preferences, Appearance), in the Theme tab click Customize, Colors, and from there you should be able to change the text color (next to Input boxes). I've come across a few themes that don't allow you to change this though.

---

### Post by CrusaderAD on 2009-08-13
> **oldos2er said:**
> Open the Appearance app (System, Preferences, Appearance), in the Theme tab click Customize, Colors, and from there you should be able to change the text color (next to Input boxes). I've come across a few themes that don't allow you to change this though.

Yep, I've seen that. It doesn't let me change it. Know of a way to do it by editing the themes configuration manually?

---

### Post by stinkeye on 2009-08-13
> **raptormanad said:**
> Yep, I've seen that. It doesn't let me change it. Know of a way to do it by editing the themes configuration manually?

Sorry I don't, but I know all the info is in the gtkrc file in the .themes folder.
Maybe you could post a message to the creator at [http://www.gnome-look.org/](http://www.gnome-look.org/) on how to change the color in the gtkrc.
What theme are you using?

---

### Post by CrusaderAD on 2009-08-13
> **stinkeye said:**
> What theme are you using?

QDark, it's kinda like Slickness-Black.

---

### Post by stinkeye on 2009-08-13
Ok I see what you mean by the dark fields in firefox.I use opera so  dont have this problem.
I did a google search and came across this [http://ubuntusatanic.org/forum/comments.php?DiscussionID=106&page=1](http://ubuntusatanic.org/forum/comments.php?DiscussionID=106&page=1)
I am sure there is afew solutions out there.
This page specifically tells you how to change the dark input boxes:
[http://ubuntusatanic.org/dark-themes.php]("http://ubuntusatanic.org/dark-themes.php")

---

### Post by CrusaderAD on 2009-08-13
Woohoo! This worked. Thanks stinkeye!

```

So here is how you fix firefox 3:

navigate to ./mozilla/firefox/~/chrome and open userContent-example.css

Then add my code to the end:

/* Smooth Scrolling Workaround: Disable Fixed Background Images on Pages */
body {
background-attachment: scroll !important;
}

input {
border: 2px inset white;
background-color: white;
color: black;
-moz-appearance: none !important;
}

textarea {
border: 2px inset white;
background-color: white;
color: black;
-moz-appearance: none !important;
}

select {
border: 2px inset white;
background-color: white;
color: black;
-moz-appearance: none !important;
}

input[type="radio"],
input[type="checkbox"] {
border: 2px inset white ! important;
background-color: white ! important;
color: ThreeDFace ! important;
-moz-appearance: none !important;
}

*|*::-moz-radio {
background-color: white;
-moz-appearance: none !important;
}

button,
input[type="reset"],
input[type="button"],
input[type="submit"] {
border: 2px outset white;
background-color: #eeeeee;
color: black;
-moz-appearance: none !important;
}

body {
background-color: white;
color: black;
display: block;
margin: 8px;
-moz-appearance: none !important;
}


Then save the edited file as userContent.css

```

---

### Post by stinkeye on 2009-08-13
> **raptormanad said:**
> Woohoo! This worked. Thanks stinkeye!

```

So here is how you fix firefox 3:

navigate to ./mozilla/firefox/~/chrome and open userContent-example.css

Then add my code to the end:

/* Smooth Scrolling Workaround: Disable Fixed Background Images on Pages */
body {
background-attachment: scroll !important;
}

input {
border: 2px inset white;
background-color: white;
color: black;
-moz-appearance: none !important;
}

textarea {
border: 2px inset white;
background-color: white;
color: black;
-moz-appearance: none !important;
}

select {
border: 2px inset white;
background-color: white;
color: black;
-moz-appearance: none !important;
}

input[type="radio"],
input[type="checkbox"] {
border: 2px inset white ! important;
background-color: white ! important;
color: ThreeDFace ! important;
-moz-appearance: none !important;
}

*|*::-moz-radio {
background-color: white;
-moz-appearance: none !important;
}

button,
input[type="reset"],
input[type="button"],
input[type="submit"] {
border: 2px outset white;
background-color: #eeeeee;
color: black;
-moz-appearance: none !important;
}

body {
background-color: white;
color: black;
display: block;
margin: 8px;
-moz-appearance: none !important;
}


Then save the edited file as userContent.css

```
No problem.
To help someone fills my heart with glee.Teehee.

---

### Post by WetWired on 2009-09-10
> **stinkeye said:**
> gnome-color-chooser

I love you. :lolflag:

---

