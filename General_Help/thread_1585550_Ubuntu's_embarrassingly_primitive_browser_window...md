---
title: "Ubuntu's embarrassingly primitive browser window..."
date: 2010-09-30
forum: General Help
---

### Post by neu5eeCh on 2010-09-30
**Description: **I use WordPress. If I want to choose an image to insert into the blog, the file browser window (unlike even the most basic version of Windows) only gives me a "list view" option and no other options. This.Is.A.Huge.Limitation. I can't choose an image visually - only by name.

**Question: **Is there a way to remedy this? Will a different file browser (instead of Nautilus?) get me what I want?

---

### Post by gallifrey on 2010-09-30
Try nautilus elementary:

> sudo add-apt-repository [B]ppa:am-monkeyd/nautilus-elementary-ppa

sudo apt-get update

sudo apt-get upgrade
[/B]

---

### Post by QIII on 2010-09-30
Going from memory (not at an Ubuntu box at the moment), so bear with me.

In Nautilus, click Edit | Preferences | Preview tab.

Make sure "Show Thumbnails" is set to "Always" and look at the file size box to see if you need to increase the size to make sure you are getting large file sizes included.

I hope I got that close to right.  The memory is the first thing to go...

---

### Post by coffeecat on 2010-09-30
> **VTPoet said:**
> the file browser window (unlike even the most basic version of Windows) only gives me a "list view" option and no other options.

Do you mean that Nautilus is not offering you icon or compact view under the View menu? If so, that is not normal behaviour.

---

### Post by QIII on 2010-09-30
> **coffeecat said:**
> If so, that is not normal behaviour.

It certainly isn't.  Otherwise, I wouldn't be embarrassed when my wife walks in and I am browsing my "special hidden folder"...

;)


BTW --  I don't know where I dredged my answer from in the deep recesses of my brain.  Icon view should be in the drop down.

---

### Post by neu5eeCh on 2010-09-30
> **QIII said:**
> Going from memory (not at an Ubuntu box at the moment), so bear with me.

In Nautilus, click Edit | Preferences | Preview tab.

Make sure "Show Thumbnails" is set to "Always" and look at the file size box to see if you need to increase the size to make sure you are getting large file sizes included.

Thanks, that was the first thing I tried, but it doesn't *seem* to change the behavior of a browser window **if**, for example, you click browse from another program like OO. 

> **QIII said:**
> I hope I got that close to right.  The memory is the first thing to go...

I thought hair was the first thing to go.

---

### Post by neu5eeCh on 2010-09-30
> **coffeecat said:**
> Do you mean that Nautilus is not offering you icon or compact view under the View menu? If so, that is not normal behaviour.

Not quite. It's not offering me a choice **if** another program calls up a browse window. For instance, go to OO --> File --> Open.

Even key combinations, like Cntrl 1, won't work.

---

### Post by neu5eeCh on 2010-09-30
> **QIII said:**
> It certainly isn't.  Otherwise, I wouldn't be embarrassed when my wife walks in and I am browsing my "special hidden folder"...

;) 

Ah... yes. Perfect. You shall be my control.

Do this: If you have GIMP, go to File --->Open. Then navigate to your hidden folder. You will see a preview pane on the right.

That's OK, but not ideal. It would be better to simply *see* the images. Right?

Now, if you have OO, go to Insert ---> Picture ---> From File.

Now, navigate to the same hidden folder and all you will see are tiny, tiny, tiny little XXX thumbnails. They are of no use. There will be no preview pane and no option to **see** the image.

---

### Post by neu5eeCh on 2010-09-30
> **gallifrey said:**
> Try nautilus elementary:


[/B]

I will try that.

**Edit: **Didn't work, but thanks.

---

### Post by QIII on 2010-09-30
I'll try that when I get home.  

I won't send you any screenshots, because this is a family forum...

I guess I've never tried this in OO.  This may be less a Nautilus problem than the way OO invokes Nautilus.  Would be interesting to find out.


(If I had that special folder, I'd come home one day to find my belongings on the lawn burning.  ;))


EDIT:  This looks promising:

[http://www.sktesabajang.co.cc/2009/09/nautilus-icons-enable-openoffice-documents-with-real-preview](http://www.sktesabajang.co.cc/2009/09/nautilus-icons-enable-openoffice-documents-with-real-preview)

---

### Post by neu5eeCh on 2010-09-30
> **QIII said:**
> (If I had that special folder, I'd come home one day to find my belongings on the lawn burning.  ;))

Yes, of course... plausible deniability is of the essence.

---

### Post by SeijiSensei on 2010-09-30
If you've just started down the road with Ubuntu, I recommend trying the KDE desktop instead of GNOME.  It has many of the features you're looking for.  Install the "kde-desktop" package either through your software installer, or from a Terminal if you're comfortable with that by typing the command 'sudo apt-get install kde-desktop'.  

Reboot after it's finished, and when the login screen appears you should have an icon that enables you to choose KDE instead.  Give it a whirl.

If you just installed Ubuntu recently and aren't averse to reinstalling over it, the Kubuntu flavor uses KDE by default.  Alternatively just download the [Kubuntu CD]("http://cdimage.ubuntu.com/kubuntu/releases/lucid/release/") and boot it.  You can see what it would look like on your machine without actually installing it.

You'll also probably enjoy using the Gwenview image viewer and manager.

I'm very discouraged by how few people even seem to know that KDE exists much less try it out.  It's been my preferred desktop for years.

---

### Post by QIII on 2010-09-30
KDE may not be of much help if this is a limitation of OO.

---

### Post by neu5eeCh on 2010-09-30
> **QIII said:**
> KDE may not be of much help if this is a limitation of OO.

It's not a limitation of OO. The problem seems to be a combination of nautilus & gnome.

I've been toying around with Fedora KDE on a second partition, and I must admit that KDE is growing on me. I prefer the simplicity of Gnome's menu system, but some of these very basic limitations are beginning to rankle.

I might just do as Seiji suggests. At the moment, I am upgrading 10.04 to release candidate 10.10. Why not? All my files are backed up. Let's see what, if anything, improves? If nautilus is still a drag, then I'm going to install the KDE desktop.

In the meantime, any more ideas for fixing this limitation in gnome?

---

### Post by SeijiSensei on 2010-09-30
> **VTPoet said:**
> I prefer the simplicity of Gnome's menu system, but some of these very basic limitations are beginning to rankle.

Wow, that's one of the things that annoys me about GNOME -- all the programs aren't in one place.  I always have to look in Applications and System to find what I'm looking for.  In KDE there's just one menu for all the software, and it's in the same place as it is in Windows. :roll: (Not that I really care anymore; I've used Windows perhaps 10-50 hours per year over the past decade and only for work-related purposes.)

---

### Post by neu5eeCh on 2010-09-30
> **SeijiSensei said:**
> Wow, that's one of the things that annoys me about GNOME -- all the programs aren't in one place.  I always have to look in Applications and System to find what I'm looking for.  In KDE there's just one menu for all the software, and it's in the same place as it is in Windows. :roll: (Not that I really care anymore; I've used Windows perhaps 10-50 hours per year over the past decade and only for work-related purposes.)

I've probably just gotten used to it.

For me, I feel like I have to *dig around* in KDE's one menu system. As with anything, though, I think one accommodates oneself.

---

### Post by QIII on 2010-09-30
> **VTPoet said:**
> There will be no preview pane and no option to **see** the image.

Actually, I have the option to view in a preview pane.

But the thumbnails are definitely tiny.

---

### Post by neu5eeCh on 2010-09-30
Is it a preview pane or is it small icons? If you use GIMP, the preview pane is to the right (there are **two** panes) and provides an actual, viewable, reduction of the image.

**Edit:** Also, with which program are you launching the browser?

---

### Post by neu5eeCh on 2010-09-30
> **SeijiSensei said:**
> Wow, that's one of the things that annoys me about GNOME -- all the programs aren't in one place.  I always have to look in Applications and System to find what I'm looking for.  In KDE there's just one menu for all the software, and it's in the same place as it is in Windows. :roll: (Not that I really care anymore; I've used Windows perhaps 10-50 hours per year over the past decade and only for work-related purposes.)

Hey Seiji, I'm typing this from my KDE desktop. Lovely. Really lovely...

Especially if one immediately uses Emerald. KWIN's window borders are dull as ditch water.

Unfortunately, KDE's browsing window behaves just like Gnomes. When I open a browsing window from a "third party" app there's no option to view files as icons. It's possible that because I have gnome and KDE installed side by side, that the apps are still opening nautilus?

What happens on **your** system?

Also, a possible solution might be gloobus. BUT... I just installed 10.10 and libpoppler5 is unavailable for 10.10 (meaning that gloobus can't be installed due to unresolved dependencies). :rolleyes:

---

### Post by QIII on 2010-10-01
It's an actual preview pane to the right.  Doing it in OO Write (or whatever it's called).

---

