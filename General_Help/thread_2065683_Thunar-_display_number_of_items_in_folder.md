---
title: "Thunar- display number of items in folder?"
date: 2012-10-02
forum: General Help
---

### Post by mrsfixit on 2012-10-02
I am using Xubuntu 12.04 on my notebook.

I use the detailed list view in Thunar. Is there a way to make Thunar display the number of items in a subdirectory like Nautilus does?

When I open up a folder, all it says is "4.1kb" for every subdirectory, which isn't helpful in the least. 

I have searched for an answer, but have found nothing.

Any help appreciated.

---

### Post by The Cog on 2012-10-02
It does in 12.10 (beta2) if that's any help. I guess it's a new feature in the later version.

---

### Post by mrsfixit on 2012-10-02
> **The Cog said:**
> It does in 12.10 (beta2) if that's any help. I guess it's a new feature in the later version.

That's good to know.

I do plan on upgrading to 12.10, but to a final release, not a beta.

It would be nice if there was some way to implement this in 12.04 though...

I have no patience and hate to wait... :p

Thanks for the info though. At least I'll have something to look forward to. ;)

---

### Post by LewisTM on 2012-10-02
12.10 features Xfce 4.10 with the updated Thunar.
You can install a perfectly stable and functional Xfce 4.10 in Ubuntu 12.04 with this [PPA]("https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10").
For those who cannot wait:
```
sudo apt-add-repository ppa:xubuntu-dev/xfce-4.10 -y && sudo apt-get update && sudo apt-get dist-upgrade -y
```
Cheers!

---

### Post by mrsfixit on 2012-10-02
> **LewisTM said:**
> 12.10 features Xfce 4.10 with the updated Thunar.
You can install a perfectly stable and functional Xfce 4.10 in Ubuntu 12.04 with this [PPA]("https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10").
For those who cannot wait:
```
sudo apt-add-repository ppa:xubuntu-dev/xfce-4.10 -y && sudo apt-get update && sudo apt-get dist-upgrade -y
```Cheers!

Ok, I just ran that command and did the updates, Thunar is still only showing 4.1kb for subdirectories...

I rebooted, and checked Thunar's preferences, and don't see any difference from before.

Maybe I'm supposed to have some other package installed as well to enable newer features?

---

### Post by LewisTM on 2012-10-02
Hmm I think you have been misled. Thunar will display the total number and size of items on it's status bar, not in the details list. I don't see that being changed in 4.10 or in the beta.
I would venture to say that NOT displaying that info is part of what makes Thunar significantly faster than Nautilus. Digging through subdirectories while preparing to display a file list surely takes its toll...

---

### Post by mrsfixit on 2012-10-02
> **LewisTM said:**
> Hmm I think you have been misled. Thunar will display the total number and size of items on it's status bar, not in the details list. I don't see that being changed in 4.10 or in the beta.
I would venture to say that NOT displaying that info is part of what makes Thunar significantly faster than Nautilus. Digging through subdirectories while preparing to display a file list surely takes its toll...

Ah, so I see.

It would be nice if it was an option. I use that a lot in Nautilus, as I still run Ubuntu Lucid on my desktop computer.

Thunar lacks some of the better features of Nautilus such as dual pane view and the aforementioned option for showing the number of items in a sub-folder.

As for being faster, Thunar seems about the same speed as Nautilus, but then again, my desktop machine has a faster cpu and more ram, so that may account for it.

Thanks anyway. :p

---

### Post by The Cog on 2012-10-03
Oops. My apologies to mrsfixit - it seems I misunderstood the question. Yes, I see the item count in the status line. And now I'm on a 12.04 box, I see it's the same there as it is on 12.10.

---

### Post by thaitang on 2013-03-05
> **mrsfixit said:**
> Ah, so I see.

It would be nice if it was an option. I use that a lot in Nautilus:p
Agree. That would be nice if it was a feature. But hey tab browsing is what brought me back to Thunar from my daily dependence on Nautilus. But often I run a script that d/loads files to multiple dirs and it is nice in Naut to simply have the parent dir open and see how many files are in its sub-dirs as a quick way to check progress without clicking on each file.

Actually for me, there are no file content details displayed in the status bar in Thunar, but I always run LTS, so I guess it must be a feature in 12.10, which I will see in the next LTS release. 

Although I can live without the dual-pane view, I too use that regularly while using Naut, but tabs in Thunar is enough like I said to make it my default fm.

---

### Post by mrsfixit on 2013-03-08
> **thaitang said:**
> Agree. That would be nice if it was a feature. But hey tab browsing is what brought me back to Thunar from my daily dependence on Nautilus. But often I run a script that d/loads files to multiple dirs and it is nice in Naut to simply have the parent dir open and see how many files are in its sub-dirs as a quick way to check progress without clicking on each file.

Actually for me, there are no file content details displayed in the status bar in Thunar, but I always run LTS, so I guess it must be a feature in 12.10, which I will see in the next LTS release.

Although I can live without the dual-pane view, I too use that regularly while using Naut, but tabs in Thunar is enough like I said to make it my default fm.

I had to finally put my install of Ubuntu Lucid to rest and replace it with Xubuntu 12.10, as I just can't abide Unity. 

There were just too many programs I needed to upgrade and couldn't in Lucid.

There are file content details displayed on the statusbar in Thunar in 12.10, but  only if you open a folder. Thunar will simply display the number of  items, and their total size. I don't find it all that helpful TBH.

I am really missing the dual pane view in Nautilus. Tabs is nice but I don't use it as much as I did the dual pane view. I also really miss the little arrow on the Nautilus folders that would let you see the folder contents without actually having to open it.

The Thunar dev's said they would never add tabs, so who knows- maybe they'll give in on the dual pane view eventually as well. I know  lot of people have asked for the feature.

I know I could use Nautilus as a fm in Xubuntu instead of Thunar, but doing that will introduce it's own set of problems and I don't feel it's worth it.

My system is running quite nicely right now and I'd like to keep it that way... :P

---

