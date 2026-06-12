---
title: "How Can I Change Ubuntu 10.04's Theme to 9.10's?"
date: 2010-05-01
forum: General Help
---

### Post by Joseph Schwenker on 2010-05-01
After my first boot of Ubuntu 10.04, a certain thing caught my eye, the fugly theme.  In 9.10, I used Humanity for controls and Lucidity for the Window border, but after downloading the Humanity icons and the control theme, there are still icon elements that remain themed with the fugly 10.04 theme.  My icons in my home folder alternate between 9.10 and 10.04 when I zoom in and out.  I still have the fugly plus and minus buttons instead of the nice flippy triangles.  Additionally, applications that run in root are not themed with my theme configuration.  Can anyone help me solve this?

---

### Post by MichealH on 2010-05-01
The programs running as root is what root has so you would have to change your root theme which I wouldnt reccomend. You could get your 9.10 cd and copy files across thats the Humanity theme ect. to lucid.

---

### Post by Joseph Schwenker on 2010-05-01
> **MichealH said:**
> The programs running as root is what root has so you would have to change your root theme which I wouldnt reccomend. You could get your 9.10 cd and copy files across thats the Humanity theme ect. to lucid.

Why is it that in 9.10, root applications used the theme that I used, and now they don't?!  How do I change my root theme?  Where is the Humanity theme on the Ubuntu 9.10 disc?

---

### Post by MichealH on 2010-05-01
The files will be mounted at boot I beleive. Also, To change the roots theme try to change the roots password and get in by logging out clicking "Other" type in root for user and the pass you entered then change the theme.

---

### Post by Joseph Schwenker on 2010-05-01
I looked on my 9.10 install cd, and found nothing labeled "boot".  I was able to get root applications running with my theme using another person's tutorial.

---

### Post by Joseph Schwenker on 2010-05-01
Do you know of a download link for the file?  I am REALLY getting sick of the occassional red folders as well as the fugly plus and minus buttons.  It's like they're just sitting there, taunting me.
 ++
\--/

---

### Post by Joseph Schwenker on 2010-05-01
I just found a link to download 9.10's Human theme, but it STILL does not replace the plus and minus buttons with the flippy triangles.  Can anyone help?

---

### Post by Joseph Schwenker on 2010-05-03
I've found the same problem here: [https://bugs.launchpad.net/ubuntu/+source/human-theme/+bug/527789](https://bugs.launchpad.net/ubuntu/+source/human-theme/+bug/527789)

Does anyone know how to apply the patches that they are talking about?

---

### Post by Joseph Schwenker on 2010-05-04
bump

---

### Post by MichealH on 2010-05-07
Sorry but I dont know, I would try to subscribe to the bug to see if I can fix it or something.

---

### Post by Joseph Schwenker on 2010-05-14
bump

I think it has something to do with different rendering engines, or something like that.

---

### Post by MichealH on 2010-05-15
Thinking about it yes, It will be because it is a newer version of Metacity :roleyes: Why didn't I think of that before?

---

### Post by Joseph Schwenker on 2010-05-15
The thing is, I can get the flippy triangles if I use a different theme.  If I use Raleigh, Redmond, Simple, or New Wave, I can get those flippy triangles.  However, I want the flippy triangles in the Human theme.

---

### Post by MichealH on 2010-05-15
Just to ask but what flippy tiangles?

---

### Post by Joseph Schwenker on 2010-05-15
The flippy triangles that you click on in the list view in Nautilus to expand a folder.  You click on it, and it flips to a down position to indicate that the folder is expanded.  They do the same thing as + and - buttons, but I like the triangles better.

---

### Post by MichealH on 2010-05-15
> **Joseph Schwenker said:**
> The flippy triangles that you click on in the list view in Nautilus to expand a folder.  You click on it, and it flips to a down position to indicate that the folder is expanded.  They do the same thing as + and - buttons, but I like the triangles better.

Then I think it is an Icon file OR A nautilus file.

---

### Post by Joseph Schwenker on 2010-05-17
bump

---

### Post by MichealH on 2010-05-18
I dont have a clue now so I will look it up but no guarantee.

---

### Post by Joseph Schwenker on 2010-05-18
bump

---

### Post by Joseph Schwenker on 2010-05-29
If I use other themes, I can get the flippy triangles, but not in 9.10's Humanity theme.

---

### Post by MichealH on 2010-05-30
Was there Flippy Triangles in 9.10?

---

### Post by Joseph Schwenker on 2010-05-30
Yes.  And it's "were there", not "was there".  I am a Grammar Nazi.

---

### Post by Wardje on 2010-05-30
Assuming it's themebased, my guess would be you'd need to go make a change in ```
/usr/share/icons
```... somewhere. It's a maze of icons for different skins D:

---

### Post by Joseph Schwenker on 2010-05-30
You're right.  It IS a maze.

---

### Post by Joseph Schwenker on 2010-06-12
Bump.
I still need help on this.

---

### Post by Joseph Schwenker on 2010-06-15
Since no one seems to care about the extremely awful taste of the interface designers of Ubuntu 10.04 (Omg! Ubuntu is probably to blame, I can't go on their blog without seeing the word "sexy" written next to every interface that is more ugly than Aging Gorilla and High Contract combined), I have switched my theme to Elementary for icons, GTK+, and Metacity.  It really is quite beautiful, and it has the flippy triangles.  There are some minor problems in /usr/share/themes/elementary that can be easily fixed with Gimp, like the line under the panel, and the lines under menus on the menubar.  Unfortunately, I haven't found a way to fix the Weather icons used by the weather applet in Docky.  It seems to be using the low-res, monochrome ones when I use Elementary Monochrome.

---

### Post by amilanov on 2010-09-17
I was in a similar situation after I installed 10.04.
 
 What I did is I installed the old versions of the themes and all worked out well. I have written a step-by-step guide on that - [http://amilanov.com/articles/how-to-make-ubuntu-10.04-look-like-9.10/](http://amilanov.com/articles/how-to-make-ubuntu-10.04-look-like-9.10/).
 
 The flippy triangles are actually part of the old Human-Clearlooks theme from 9.10. So, if you get it back and install Lucidity, you can combine them - go to Appearance Preferences, select Human-Clearlooks, then Customize and change Window Border to Lucidity.

---

### Post by Joseph Schwenker on 2010-09-17
> **amilanov said:**
> I was in a similar situation after I installed 10.04.
 
 What I did is I installed the old versions of the themes and all worked out well. I have written a step-by-step guide on that - [http://amilanov.com/articles/how-to-make-ubuntu-10.04-look-like-9.10/](http://amilanov.com/articles/how-to-make-ubuntu-10.04-look-like-9.10/).
 
 The flippy triangles are actually part of the old Human-Clearlooks theme from 9.10. So, if you get it back and install Lucidity, you can combine them - go to Appearance Preferences, select Human-Clearlooks, then Customize and change Window Border to Lucidity.

Thanks!  This looks like it will work great.

---

