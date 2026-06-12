---
title: "Desktop Launcher to Web Page"
date: 2012-02-08
forum: General Help
---

### Post by Quarkrad on 2012-02-08
Running 10.10.  I have a number of desktop launchers for my father-in-law that go direct to specific web pages.  I right click and create a launcher using the command:  firefox [http://*the web page*](http://*the web page*).  This works very well.  I am trying to do this same thing for him to access the virgin media sign-in page.  I have booked marked the page in firefox and can go there every time, even after rebooting.  The url is a ridiculous: [https://identity.virginmedia.com/vm_sso/idp/requestAssertion.action?SAMLRequest=eJx9kV9rwjAUxb9KybttlQkSTMVtjAk6ilYf9pamtzWl%2BbPctGzfftFOcHsYJA9J7jn33F%2BWq0%2FVRQM4lEYzMo1TEoEWppK6YeRYvEwWZJUtkavO0nXvz3oPHz2gj4JOI70%2BMNI7TQ1HiVRzBUi9oIf1bktncUqtM94I05FojQjOh0ZPRmOvwB3ADVLAcb9l5Oy9RZok6isepGukVlBJHgujEi7wskm0eWbE1s25aWtbgq5KXpaiqdoGahBW2dLYtjXKiLbjoRpzjigHYKTmHcLlBnvYaPRce0Zm6XQ2ScNaFNM5fZjT%2BeKdRPlP3EepRwh%2FZovvZyvHIqSvRZFP9iGxA%2BGvJoOswL0FBSOnXW6c54HA6QY6iMmIlV5DuTue%2F%2BPkN4gku%2FkukzujbDz9%2Fq3sGyBZqus%3D&RelayState=https%3A%2F%2Fmy.virginmedia.com%2Fhome%2Findex](https://identity.virginmedia.com/vm_sso/idp/requestAssertion.action?SAMLRequest=eJx9kV9rwjAUxb9KybttlQkSTMVtjAk6ilYf9pamtzWl%2BbPctGzfftFOcHsYJA9J7jn33F%2BWq0%2FVRQM4lEYzMo1TEoEWppK6YeRYvEwWZJUtkavO0nXvz3oPHz2gj4JOI70%2BMNI7TQ1HiVRzBUi9oIf1bktncUqtM94I05FojQjOh0ZPRmOvwB3ADVLAcb9l5Oy9RZok6isepGukVlBJHgujEi7wskm0eWbE1s25aWtbgq5KXpaiqdoGahBW2dLYtjXKiLbjoRpzjigHYKTmHcLlBnvYaPRce0Zm6XQ2ScNaFNM5fZjT%2BeKdRPlP3EepRwh%2FZovvZyvHIqSvRZFP9iGxA%2BGvJoOswL0FBSOnXW6c54HA6QY6iMmIlV5DuTue%2F%2BPkN4gku%2FkukzujbDz9%2Fq3sGyBZqus%3D&RelayState=https%3A%2F%2Fmy.virginmedia.com%2Fhome%2Findex)

When I put this into the launcher I get a virgin page that says **An unexpected error has occurred**.  What intrigues me is that this url works every time as a bookmark but not as a desktop launcher - why is this?

---

### Post by jamesisin on 2012-02-08
This is just a guess but I would try removing the % replacements for their actual characters.  I'm guessing they are being passed to Ff incorrectly.

---

### Post by Quarkrad on 2012-02-09
Thanks - when I posted this the url address was in it's long individual character form but when I pasted it into this post it converted itself to the form above.  See attached for a picture of the actual address.  You can 'see' what I'm talking about by bookmarking the VirginMedia sign-in page and also creating a Desktop launcher with the same address.  The launcher will not go the the page but the bookmark will.  This is the first address this has happened to me.

---

### Post by jamesisin on 2012-02-10
Can you paste that URL into a code box so I can try it here?

---

### Post by Quarkrad on 2012-02-10
Thanks for the help - forgot to say I'm a newbie, unfortunately I do know how to create/access a 'code box'.  If you go to this page **[http://my.virginmedia.com/home/index](http://my.virginmedia.com/home/index)** and click on the red **Sign in** button (next to this button there is a grey box/button called Register) you will get to the page I'm talking about.  It's accessible all the time when you bookmark it but not when you use this same code in a launcher (well for me that is).

---

### Post by Thorsen V on 2012-02-10
[B]perhaps replace the troublesome link  with a tinyurl, or your preferred URL shorter?

eg this page becomes: [http://tinyurl.com/6tyuq5b](http://tinyurl.com/6tyuq5b)[/B]

---

### Post by Quarkrad on 2012-02-10
I haven't come accross this before - can you point me to somewhere were I can read up on this please?  How is this done ? Looks a little spooky.

---

### Post by Thorsen V on 2012-02-10
This method also appears to work. In a terminal do something like:

gedit ~/Desktop/link.desktop &

Then add these lines:[INDENT][FONT=Courier New][Desktop Entry][/FONT]
[FONT=Courier New] Encoding=UTF-8[/FONT]
[FONT=Courier New] Icon=text-html[/FONT]
[FONT=Courier New] Type=Link[/FONT]
[FONT=Courier New] Name=redonculous link![/FONT]
[FONT=Courier New] URL=https://identity.virginmedia.com/vm_sso/idp/requestAssertion.action?SAMLRequest=eJx9kV9rwjAUxb9KybttlQkSTMVtjAk6ilYf9pamtzWl%2BbPctGzfftFOcHsYJA9J7jn33F%2BWq0%2FVRQM4lEYzMo1TEoEWppK6YeRYvEwWZJUtkavO0nXvz3oPHz2gj4JOI70%2BMNI7TQ1HiVRzBUi9oIf1bktncUqtM94I05FojQjOh0ZPRmOvwB3ADVLAcb9l5Oy9RZok6isepGukVlBJHgujEi7wskm0eWbE1s25aWtbgq5KXpaiqdoGahBW2dLYtjXKiLbjoRpzjigHYKTmHcLlBnvYaPRce0Zm6XQ2ScNaFNM5fZjT%2BeKdRPlP3EepRwh%2FZovvZyvHIqSvRZFP9iGxA%2BGvJoOswL0FBSOnXW6c54HA6QY6iMmIlV5DuTue%2F%2BPkN4gku%2FkukzujbDz9%2Fq3sGyBZqus%3D&RelayState=https%3A%2F%2Fmy.virginmedia.com%2Fhome%2Findex[/FONT]
[FONT=Courier New] [InternetShortcut][/FONT]
[/INDENT][FONT=Verdana]Save, and now on your desktop you should see an icon called "redonculous link!" that you should be able to just click on to open the link in your default browser.
[/FONT]

---

### Post by Thorsen V on 2012-02-10
> **Quarkrad said:**
> I haven't come accross this before - can you point me to somewhere were I can read up on this please?  How is this done ? Looks a little spooky.
tinyurl is a link shortening service. It lets you add a button to your firefox tool bar (see: [https://addons.mozilla.org/en-US/firefox/addon/tinyurl-creator/](https://addons.mozilla.org/en-US/firefox/addon/tinyurl-creator/)) that you then just click on while viewing a page and will make one of these short easier to remember/quote, links for you.

Its useful with emails etc especially with silly urls like this one :D

There are definitely pros and cons with URL shorteners; the main con I think is you are reliant on the service continuing: If tinyurl goes out of business all your links break!

---

### Post by Quarkrad on 2012-02-10
I like your desktop solution (actually I'm having trouble creating .desktop files that also have specific icons).  When I follow your instructions and press Save the file appears to be saved somewhere but it isn't on my Desktop.  Done it twice now.

---

### Post by Thorsen V on 2012-02-10
> **Quarkrad said:**
> I like your desktop solution (actually I'm having trouble creating .desktop files that also have specific icons).  When I follow your instructions and press Save the file appears to be saved somewhere but it isn't on my Desktop.  Done it twice now.

Sorry there was a typo :oops:

should have been:

gedit ~/Desktop/link.desktop

---

### Post by Quarkrad on 2012-02-10
Ultimately I would like to have this desktop shortcut with a virgin media icon.  I can get the picture, create it as a .png file size 48x48 and, as I understand, save it to ~/.icons.  My other issue, but alo related to this one, is linking the .desktop file to the icon and putting it into the launcher (11.10).  I have got as far as getting the desktop file and icon on my desktop but when I drag it into the launcher the icon disappears.  However, that's my other issue, I would like to get tis virginmedia URL desktop file working.

---

### Post by Quarkrad on 2012-02-10
Super - however, I'm taken to the** [https://my.virginmedia.com/home/index](https://my.virginmedia.com/home/index)** page. Did you go to the other page?

---

### Post by Thorsen V on 2012-02-10
> **Quarkrad said:**
> Ultimately I would like to have this desktop shortcut with a virgin media icon.  I can get the picture, create it as a .png file size 48x48 and, as I understand, save it to ~/.icons.  My other issue, but alo related to this one, is linking the .desktop file to the icon and putting it into the launcher (11.10).  I have got as far as getting the desktop file and icon on my desktop but when I drag it into the launcher the icon disappears.  However, that's my other issue, I would like to get tis virginmedia URL desktop file working.
Well, in Gnome 2 (I'm using 10.04 LTS), you link the icon bya  right click on the desktop launcher and select "properties" from the menu, then click on the icon preview on the left. A file selector dialogue appears so you can navigate to the icon of your choice.

Perhaps this is the same in Unity? I can't help with the unity-specific question

---

### Post by Thorsen V on 2012-02-10
> **Quarkrad said:**
> Super - however, I'm taken to the** [https://my.virginmedia.com/home/index](https://my.virginmedia.com/home/index)** page. Did you go to the other page?
Yes. (See attached.)

---

### Post by Quarkrad on 2012-02-10
Thank you very much and it does work but there is something strange.  I have given my in-laws Ubuntu and for reasons I will not go into one of them has 10.10 and the other 11.10.  My original problem with the Virgin Media url was on the 10.10 machine - I have tried your code on my 10.10 machine and it works.  I have only used the right-click gui create launcher up to this point on 10.10 and it didn't work.  Your method does work.  Is there a way I can now assign a specific icon to your redonculous link files that is now on my desktop?  The odd thing is I have a 11.10 machine running in Virtualbox on my machine so I can simulate my father-in-laws machine  hence I am in the Unity world as well as gnome world.   The odd thing is your code in 10.10 brings up the page as you proved but when the same code is done in 11.10/Unity (not 11.10 running as 10.xx) the page takes you to a different place.  Strange.

---

### Post by Thorsen V on 2012-02-10
> **Quarkrad said:**
> Thank you very much and it does work but there is something strange.  I have given my in-laws Ubuntu and for reasons I will not go into one of them has 10.10 and the other 11.10.  My original problem with the Virgin Media url was on the 10.10 machine - I have tried your code on my 10.10 machine and it works.  I have only used the right-click gui create launcher up to this point on 10.10 and it didn't work.  Your method does work.  [COLOR=Red]Is there a way I can now assign a specific icon to your redonculous link files that is now on my desktop? [/COLOR] The odd thing is I have a 11.10 machine running in Virtualbox on my machine so I can simulate my father-in-laws machine  hence I am in the Unity world as well as gnome world.   The odd thing is your code in 10.10 brings up the page as you proved but when the same code is done in 11.10/Unity (not 11.10 running as 10.xx) the page takes you to a different place.  Strange.
did you try the method as described in [http://ubuntuforums.org/showpost.php?p=11677643&postcount=14](http://ubuntuforums.org/showpost.php?p=11677643&postcount=14) ?
It ought to work if you're using G2, and I can't imagine why Unity should have changed something like this (but perhaps it has :mad:)
As for your other questions hopefully someone who uses Unity will be able to help

---

### Post by Quarkrad on 2012-02-10
Yes that works -many many thanks

---

### Post by jamesisin on 2012-02-10
For your edification...

You can create a code box be either hi-lighting the text and using the # button in the toolbar above your reply's text box or you can merely surround any text with the square bracket beginning and ending tags CODE and /CODE (enclose those in square brackets that is and the code goes in between).

---

