---
title: "Dual monitor Wallpaper"
date: 2010-05-08
forum: General Help
---

### Post by Ioky on 2010-05-08
I just upgrade to ubuntu 10.04. and notice, "Stretch" no longer work with wallpaper that made for Dual Screen. "those really long wallpaper". In the past, Stretch display the wallpaper stretch to the full resolution of monitor 1 + monitor 2. 

Now it just put the exact wallpaper on each of the display. There is a new "span" option, but that is totally a non sense option. It put any wallpaper right at the middle of the two display. Who will ever do that? it is good if you have a wallpaper that is exactly the size of your two monitor combine, but nothing else. 

I just wondering is there anything I can do to fix this problem. This really sounds like Bug more than a design error. But if it really is the way it got designed, than, it is a bad design idea. it really is. haha 

Thanks for the help.

---

### Post by detrate on 2010-05-08
I also just discovered this and found it upsetting.  I haven't come across a solution yet.

---

### Post by Ioky on 2010-05-09
it might seem a very little problem. But it indeed upset me too. I think there are two patch for this. but I have no idea how to patch thing, yet.

---

### Post by tnt533 on 2010-05-09
I just noticed this myself while getting things setup for the first time this morning... I have wallpaper files of various sizes and Ubunutu used to just simply stretch the file out to fit both screens.

I would like to see a solution to this as well.

The stretch function still works if your wallpaper image file is of the appropriate size for both displays.

---

### Post by flyingmonkey35 on 2010-05-09
frist off what video card are you using?
 
im runnign a nivida gx250 and have now issues with dual moniters. in 10.

---

### Post by jlintz on 2010-05-09
also seeing this issue.   Hopefully someone will find a workaround soon

---

### Post by Ioky on 2010-05-09
Silly work around Just use GIMP to size the wallpaper to the full resolution as both of your monitor combine. 

I know... it is silly and stupid... But it is the only things that work. Or you can patch it yourselves. which I have no idea how. haha

---

### Post by Roasted on 2010-05-12
> **Ioky said:**
> Silly work around Just use GIMP to size the wallpaper to the full resolution as both of your monitor combine. 

I know... it is silly and stupid... But it is the only things that work. Or you can patch it yourselves. which I have no idea how. haha

That's what I did, and yet I still have this problem.

Example:

Monitor 1 = 1920x1080
Monitor 2 = 1440x900

So therefore I make a canvas of 3360x1080 and just paste the two images in accordingly and save as 1 image. Then I apply as background and up until (and including) 9.10 it worked fine. However, now no matter WHAT wallpaper I apply, it applies to BOTH screens each and every time. If I apply my "combo" wallpaper (the 3360x1080 one) it shows that entire instance on each monitor.

Meaning if I make a custom 3360x1080 wallpaper of a Corvette on the left + Mustang on the right, it crunches that entire wallpaper onto each monitor - so I see Corvette/Mustang on Monitor 1 and Corvette/Mustang on Monitor 2.

Sigh...

---

### Post by Ioky on 2010-05-12
> **Roasted said:**
> That's what I did, and yet I still have this problem.

Example:

Monitor 1 = 1920x1080
Monitor 2 = 1440x900

So therefore I make a canvas of 3360x1080 and just paste the two images in accordingly and save as 1 image. Then I apply as background and up until (and including) 9.10 it worked fine. However, now no matter WHAT wallpaper I apply, it applies to BOTH screens each and every time. If I apply my "combo" wallpaper (the 3360x1080 one) it shows that entire instance on each monitor.

Meaning if I make a custom 3360x1080 wallpaper of a Corvette on the left + Mustang on the right, it crunches that entire wallpaper onto each monitor - so I see Corvette/Mustang on Monitor 1 and Corvette/Mustang on Monitor 2.

Sigh...

It works for me when I use the "Span" Style. but nothing else. Don't really know why no developer really care about this issue. it is super basic, and they can't even do it right. I would do it myself, if I know all places that needed to be fix. If I am not mistaking there are sever places you need to fix, in order to make it works. I don't really know the GNOME coding structure. 

Try hard not to complain. haha, but sometime... there are something really bugging. I mean if they choose to do it, they should do it right. After all it is just the matter of using option A or option B. but they choose to use the wrong one. 

Really everything is working until they try to do something "to make it better". I doesn't really mind to not have all this fancy way to setup dual monitor wallpaper. But they way it works now. Almost works for no one, but the people who have two monitors that is identical. at least the same resolution. 

In the old way. It actually makes a little bit of sense. It just put a wallpaper in the screen. If the size is not big enough, it is what it is. You need a bigger one, just like would do when you change from Standard screen to wild screen. But now, they just make the decision for the user, and kind of try to out smart them. It really bugs me when decision is made by designer not user. The Good thing about GNOME is that it only give up functions, and you can config them all by yourself. You can choose to use it or not use it. And now, It is similar has to be that way. 

Sorry, If I sound going nut, but as a Designer myself. sometime, you just can't agree with something you see.

---

### Post by mudface on 2010-05-12
There is a bug filed, but it is currently unassigned:

[https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/521492](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/521492)

---

### Post by n6151h on 2010-05-15
Seeing same behaviour myself.  My "stretched" image displayed just fine across both monitors (1680x1050 each) in KK but now the best I can do in LL is "span" which spans the image across the monitors, but leaves bands at the top and bottom of the display where the image isn't tall enough to fill, vertically.

Oh, and btw, the white on grey color scheme is ugly, ubuntu.  I had it looking fine. You really didn't need to change that.

---

### Post by Roasted on 2010-05-16
Choosing "span" seemed to revert back to my old ways with it matching up my custom made large dual screen wallpapers just fine.

---

### Post by mudface on 2010-05-21
Anyone have a workaround for this besides resizing the wallpaper?

---

### Post by bodhi.zazen on 2010-05-21
> **mudface said:**
> Anyone have a workaround for this besides resizing the wallpaper?

gnome , IMO, does not do well with multiple monitors.

Would you consider xfce or kde ? Personally I found xfce works best, although I set 1 BG on each rather then gimp something together (aye you can do it w/ gimp, but I am too lazy).

---

### Post by Ioky on 2010-05-23
> **bodhi.zazen said:**
> gnome , IMO, does not do well with multiple monitors.

Would you consider xfce or kde ? Personally I found xfce works best, although I set 1 BG on each rather then gimp something together (aye you can do it w/ gimp, but I am too lazy).

Well... we all know gnome never work well with multiple monitor, but at least it has "one" way that most people wanted. And now they destroy it by decision. As far as I can see. ubuntu can patch it. 

And the point is not just go with xfce or kde. they also missing something people love about GNOME. one good little example would be the nice on panel system monitor. it is something simple, but extremely useful. both kde nor xfce have anything that come close to that. 

beside, if for someone know how where things located. it should only take them matter of minutes to get this little problem fix. solution already existed. it is up to ubuntu actually take action, and benefit everyone. instead, just let individual user to fix it themselves. 

it might sounds funny, but user sometime will give up on an OS, or Desktop, for very simple reason, such as lacking on menu editing, system monitor, or something almost sounds silly.

---

### Post by mudface on 2010-05-24
> **bodhi.zazen said:**
> gnome , IMO, does not do well with multiple monitors.

Would you consider xfce or kde ? Personally I found xfce works best, although I set 1 BG on each rather then gimp something together (aye you can do it w/ gimp, but I am too lazy).

Well, it worked perfectly in Karmic but not Lucid..

---

### Post by jetole on 2011-01-28
> **flyingmonkey35 said:**
> frist off what video card are you using?
 
im runnign a nivida gx250 and have now issues with dual moniters. in 10.

This has nothing to do with a video card. The op wasn't saying that two monitors is not working but instead that a wallpaper won't span two screens when you select the stretch option. This is a design change in Gnome itself and affects all video cards equally.

By the way, I agree that this is a pain in the but. A weak hack of a solution is to open the image in GIMP and scale it to the correct resolution of your monitor so that it fits properly with the span option but I don't think there is a proper solution yet. Someone mentioned that you can patch it but afaik there is no official patch, this is a third party patch (again, afaik) but even still, you can't expect everyone to patch Gnome.

IMHO, this wasn't a very well thought out design decision from Gnome and the dual monitor scaling should be reverted to how it was before or optionally, instead of span, there should be a check box to span that applies to whichever method you tick i.e. stretch + span, center + span, etc.

---

### Post by Brad55 on 2011-01-28
Well I guess I really didn't notice this as being a problem because I make my own wallpapers. I'm running Ubunto 10.04 64bit with a GeForce GTX 260 drivers NVIDIA UNIX x86_64 Kernel Module  195.36.24 and two monitors 1680x1050. 

Now here is something for people to think about in this first link I was running openSUSE 11.2 KDE desktop same computer I'm on now [[COLOR="RoyalBlue"]KDE Destop openSUSE 11.2[/COLOR]]("http://www.imagebam.com/image/67471288347838") and this second screen shot is the Gnome desktop again same computer [[COLOR="RoyalBlue"]Gnome desktop openSUSE 11.2[/COLOR]]("http://www.imagebam.com/image/fdec3587205714").

Now the question is how could I control 2 different desktop wallpaper one for each monitor? 

I dont care any more because I'm using Ubuntu now but just some thing for people to ponder over.

But like I said before I really know this was a problem I just make my own and it's easy and does not take a lot of time.

Here are a couple I have made just for fun. [[COLOR="RoyalBlue"]Wallpaper[/COLOR]]("http://s751.photobucket.com/albums/xx160/Brad_walls/")

---

