---
title: "How to empty trash?"
date: 2009-11-23
forum: General Help
---

### Post by Pipps on 2009-11-23
Hello

How do I empty the trash in Ubuntu Netbook Remix?

I have a fresh installation of Ubuntu Netbook Remix 9.10.

I cannot find an 'Empty Trash' icon or option anywhere. There is nothing on my panel, as there was previously in Ubuntu Desktop.

Will I be able to permanently remove all of the previously deleted files in both:
- '/home/<user>/.local/share/Trash/files; and
- '/home/<user>/.local/share/Trash/info?

I ask, as there are several MBs in both, and I only have a very limited onboard solid-state disk.

Thank you.

---

### Post by Bunnybugs on 2009-11-23
> **Pipps said:**
> Hello

How do I empty the trash in Ubuntu Netbook Remix?

I have a fresh installation of Ubuntu Netbook Remix 9.10.

I cannot find an 'Empty Trash' icon or option anywhere. There is nothing on my panel, as there was previously in Ubuntu Desktop.

Will I be able to permanently remove all of the previously deleted files in both:
- '/home/<user>/.local/share/Trash/files; and
- '/home/<user>/.local/share/Trash/info?

I ask, as there are several MBs in both, and I only have a very limited onboard solid-state disk.

Thank you.

Just select the files in trash, and remove them from there... that should help... Guess that it's just a bug... Maybe report it at [http://www.launchpad.net/](http://www.launchpad.net/)

---

### Post by wojox on 2009-11-23
Isn't there a file manager in that thing with trash on the left side. Temporarily you can run these in a terminal:

```

rm -rf /home/*/.local/share/Trash/*/** &> /dev/null
sudo rm -rf /root/.local/share/Trash/*/** &> /dev/null

```

---

### Post by kiridude on 2009-11-23
Right click on your panel and then select "add to panel." find the trash can and click "add."

---

### Post by Bunnybugs on 2009-11-23
> **kiridude said:**
> Right click on your panel and then select "add to panel." find the trash can and click "add."

NBR doesn't really have these launchers;)

---

### Post by Pipps on 2009-11-23
> **wojox said:**
> Isn't there a file manager in that thing with trash on the left side. Temporarily you can run these in a terminal:

```

rm -rf /home/*/.local/share/Trash/*/** &> /dev/null
sudo rm -rf /root/.local/share/Trash/*/** &> /dev/null

```
Thank you for the temporary fix! :)

---

### Post by Pipps on 2009-11-23
> **Bunnybugs said:**
> NBR doesn't really have these launchers;)
Indeed. :)

However, I clicked on the panel menu anyway, and selected 'Add to Menu'.

In the 'Add to Menu' window, there is no stock 'trash' option.

So I clicked on 'Custom Application Launcher'.

I now have the generic Ubuntu prompt which is asking me for the name, command, description and icon, for the custom command.

What would be the normal Ubuntu Desktop command for emptying the trash from both the '.../files' and '.../info' directories? 

In any event, could a new bespoke command be created to empty both directories anyway?

How should I formulate and enter a command for doing this?

---

### Post by barnaclebill18 on 2009-11-23
I don't know about NBR, but in Karmic, if you go to Places,Computer, Trash, there is an "Empty Trash" button top right.

---

### Post by Bunnybugs on 2009-11-23
> **barnaclebill18 said:**
> I don't know about NBR, but in Karmic, if you go to Places,Computer, Trash, there is an "Empty Trash" button top right.

Like we said, there is no such functionality in NetBookRemix... NBR is a small distribution of Ubuntu, made for the small laptops, called Netbooks... these don't have awesome resources like 2GB RAM, 250GB HDD... no, they just have the stuff to work on... not fast, but acceptable... Nothing fancy over there... all the stuff that's unusefull is left out of it!

---

### Post by Sam on 2009-11-23
> **wojox said:**
> Isn't there a file manager in that thing with trash on the left side. Temporarily you can run these in a terminal:

```

rm -rf /home/*/.local/share/Trash/*/** &> /dev/null
sudo rm -rf /root/.local/share/Trash/*/** &> /dev/null

```

More friendly version:
```
[sudo apt-get install trash-cli](apt:trash-cli)
empty-trash
```

---

### Post by Pipps on 2009-11-23
> **Bunnybugs said:**
> Like we said, there is no such functionality in NetBookRemix... NBR is a small distribution of Ubuntu, made for the small laptops, called Netbooks... these don't have awesome resources like 2GB RAM, 250GB HDD... no, they just have the stuff to work on... not fast, but acceptable... Nothing fancy over there... all the stuff that's unusefull is left out of it!
Yeah, so like he said, just move on right along, buddy. For the non-netbook user, there is nothing to see here! ;)

---

### Post by Pipps on 2009-11-23
> **Sam said:**
> More friendly version:
```
[sudo apt-get install trash-cli](apt:trash-cli)
empty-trash
```

Thank you, Sir! :)

I will give that a try this as well!

---

### Post by Pipps on 2009-11-23
> **Pipps said:**
> >  Originally Posted by Sam
More friendly version:
Code:

sudo apt-get install trash-cli
empty-trash


Thank you, Sir! :)

I will give that a try this as well!

My goodness... it works! Perfectly! :p

I installed the 'trash-cli', then created a new custom panel button, with the command specified as 'empty-trash'. Now, when I click on the new custom panel button, it deletes files from both the 'info' and 'files' trash directories! Someone please back this a NBR sticky! :)

Now all I need to find it a Karmic trash can icon for my new custom panel buttom! For that wholesome NBR completeness that we NBR users all so crave! ;)

Would anyone know where I could find the trash icon from the Karmic Desktop release? Would it be hosted online anywhere? :?

---

### Post by Bunnybugs on 2009-11-23
> **Pipps said:**
> My goodness... it works! Perfectly! :p

I installed the 'trash-cli', then created a new custom panel button, with the command specified as 'empty-trash'. Now, when I click on the new custom panel button, it deletes files from both the 'info' and 'files' trash directories! Someone please back this a NBR sticky! :)

Now all I need to find it a Karmic trash can icon for my new custom panel buttom! For that wholesome NBR completeness that we NBR users all so crave! ;)

Would anyone know where I could find the trash icon from the Karmic Desktop release? Would it be hosted online anywhere? :?

Take a look at [http://www.gnome-look.org/](http://www.gnome-look.org/)

You can download iconpackages from here, and extract just the one you need for your launcher

---

### Post by Pipps on 2009-11-23
Thank you for the link. There are definitely some very nice icon sets at GnomeLook.

But in this instances, I would prefer to just use the standard Karmic Desktop trash icon.

Would someone please attach the little trash icon file to a post for me? I would be sooo grateful! :)

---

### Post by Sam on 2009-11-23
All the system icons are in /usr/share/icons

Otherwise to set the icon according the current theme, manually edit the launcher in ~/.gnome2/panel2.d/default/launchers (it's a .desktop file), and set the icon to "gnome-fs-trash-full" or whatever file you want in /usr/share/icons (that's it, no path, no extension). Eg: Icon=gnome-fs-trash-full

---

### Post by rudy.b on 2009-11-24
> **Bunnybugs said:**
> NBR doesn't really have these launchers;)

Really?  That's strange because I've got UNR Karmic and I can add the Trash applet to the panel as normal.  Also, the Nautilus file browser has a Trash icon in the Places view on the side pane.  And there is an 'Empty Trash' command under the File menu of Nautilus as well.

---

### Post by Pipps on 2009-11-27
I have implemented my work-around fix to this problem. Please let me know if there is a better way or even a solution.

I downloaded the [Humanity Panel Icons]("http://http://www.gnome-look.org/content/show.php/Humanity+Panel+Icons+Theme?content=115260") and found the 'user-trash.svg' icon. It is an empty trash-can. It is not a perfect match with the default UNR panel icon set, but it is ok.

Also, I am not aware of any way of allowing the custom trash icon, with the commands implemented from above, to be animated so as to be empty or full.

If only the UNR 9.10 had impletmented a normal trash folder icon facility. I would have thought this would have been a priority. Surely netbooks have the smallest hard-drives of any machine on the market. Mine is just 8GB SSD!

I understand that it is freely available under the GPL, so please find it attached to this post.

I hope this might help anyone else.

---

### Post by Pipps on 2009-12-10
I have reinstalled Ubuntu Netbook Remix today.

I now have the 'Deleted Items' icon available within the 'Add to Panel' pop-up window.

Inexplicable.

---

### Post by Marc Phillips on 2010-09-02
I know this thread is a few months old, but I was just toying around with my UNR. and the Trash *still* is not intuitive to empty. And since I've been busy uploading and downloading new programs, I've also been filling up my trash quickly, which started to eat away at my SSHD.  At any rate, I was nosing through my file system when I stumbled onto the trash folder, no two locations.  Here are my steps to empty trash quickly and easily w/o dropping into terminal, feel free to improve my steps, I am a noob when it comes to ubuntu linux.

1) open up any file browser (I use the default).
2) "go to a location" ctrl + L
3) in the go to command, enter "trash://" (w/o quotes).
This is your current trash can.  
4) to empty click the button above your files.:popcorn:

---

### Post by RonCam on 2010-09-12
Very interesting thread.

Now I see, it's in Nautilus, in the Go drop-down menu: Trash.

It only took two hours to find it. ](*,)

---

### Post by Pipps on 2010-10-04
I am amazed to report that the latest Ubuntu Netbook Remix 10.04 LTS does not feature a discernible Recycle Bin icon anywhere!

Thank you Marc Phillips for the keyboard shortcut. Looks like I will have to make my own basic Recycle Bin icon again.

For an operating system which is designed specifically for 'Netbook' devices - ie computers usually possessing less than 10GB of hard disk space - it is unbelievable that the most fundamental emptying of the easily filled Recycle Bin is not given greater prominence.

It is surely the routine system maintenance task which UNR users require the most!

---

