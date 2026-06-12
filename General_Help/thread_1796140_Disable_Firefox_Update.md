---
title: "Disable Firefox Update"
date: 2011-07-03
forum: General Help
---

### Post by Tk007LwZFJW5ej on 2011-07-03
How can I prevent Firefox 5 from automatically updating itself to a new version? The relevant option is mission on the Update tab in Preferences.

---

### Post by dino99 on 2011-07-03
into synaptic, select "package" from the menu, then you can choose to block that version (after selecting "firefox")

---

### Post by ajgreeny on 2011-07-03
> **StarKid said:**
> How can I prevent Firefox 5 from automatically updating itself to a new version? The relevant option is mission on the Update tab in Preferences.
Why do you want to do this as there will be no further security updates if you do?  Are you having problems with FF updating, and if so, what are they?

---

### Post by Tk007LwZFJW5ej on 2011-07-03
> **ajgreeny said:**
> Why do you want to do this as there will be no further security updates if you do? 

I have some add-ons that are crucial to me, and I want to be able to first check whether or not they are compatible with any new firefox versions, then update manually if I so choose, or delay updating until they are compatible.

---

### Post by ajgreeny on 2011-07-03
> **StarKid said:**
> I have some add-ons that are crucial to me, and I want to be able to first check whether or not they are compatible with any new firefox versions, then update manually if I so choose, or delay updating until they are compatible.
Fair enough.  However if you go to the specific website for the add-on, there is often a patch to allow use on the new FF version almost immediately. which you can check before you do the update.

---

### Post by lovinglinux on 2011-07-04
> **StarKid said:**
> I have some add-ons that are crucial to me, and I want to be able to first check whether or not they are compatible with any new firefox versions, then update manually if I so choose, or delay updating until they are compatible.

See the Add-on section of the [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247")

---

### Post by mnemanic on 2011-12-15
I don't understand why this thread is marked as [SOLVED]. I would also like to stop Ubuntu/Firefox from automatic version updating. That doesn't mean I want to stop security updates, which was what the only "solution" posted here implied. Other replies questioned the OP's motives for wanting to disable updates and suggested some other routes for this specific user.

I have other reasons for wanting to disable the updates. One is that many webpages and online services are slow with updates for Ubuntu. When my Firefox was last updated I could no longer use one of the webpages I most frequently use, and worse, I could no longer use my electronic identification for bank/tax services etc.

On a principal level too, I want to be in command myself of what version I am using and when to change.

So, a proper solution would be appreciated.

Thanks!

---

### Post by rsvancara on 2011-12-15
You could just download the version you want from mozilla.org into your home directory, say into /home/someuser/software/Firefox_xyz and then run:

```
sudo mv /usr/bin/firefox /usr/bin/firefox_orig
sudo ln -s /home/someusers/software/Firefox_xyz/bin/firefox /usr/bin/firefox
```

Then you only update your local version when you want too.

---------------
[http://www.knowyourlinux.com/]("http://knowyourlinux.com/content/ssh-rest-us")

---

### Post by lovinglinux on 2011-12-15
> **mnemanic said:**
> I don't understand why this thread is marked as [SOLVED]. I would also like to stop Ubuntu/Firefox from automatic version updating. That doesn't mean I want to stop security updates, which was what the only "solution" posted here implied. Other replies questioned the OP's motives for wanting to disable updates and suggested some other routes for this specific user.

I have other reasons for wanting to disable the updates. One is that many webpages and online services are slow with updates for Ubuntu. When my Firefox was last updated I could no longer use one of the webpages I most frequently use, and worse, I could no longer use my electronic identification for bank/tax services etc.

On a principal level too, I want to be in command myself of what version I am using and when to change.

So, a proper solution would be appreciated.

Thanks!

Open Software Center, click "Edit >> Software Sources" in the menu, click the "Updates" tab. Configure "When there are security updates" to "Display Immediately". Configure "Automatically Check for updates" as "Never" or "Every two weeks". If you choose "Never", you will have to check for updates and update manually. If you choose "Every two weeks" you will be prompted for the updates. When that happen, select all packages except the ones related to Firefox and update.

From Firefox 10 onwards, extensions will considered compatible by default, so most likely you won't experience issues with the electronic identification. To avoid issues with web sites that doesn't recognize your browser, use [User Agent Switcher](https://addons.mozilla.org/en-US/firefox/addon/59/).

---

### Post by vasa1 on 2011-12-15
> **mnemanic said:**
> I don't understand why this thread is marked as [SOLVED]. I would also like to stop Ubuntu/Firefox from automatic version updating. That doesn't mean I want to stop security updates, which was what the only "solution" posted here implied. ....
What do you mean by Ubuntu/Firefox? Assuming you mean the Firefox that is provided with the Ubuntu installation, there's no way to get just the security updates and not the version updates for *more recent* Fx versions. IIRC, from ver. 4 onwards, older versions won't be supported. If you just want security updates, they may be available only for 3.6 (which Mozilla is desperately trying to kill off).

---

### Post by iluminameluna on 2012-01-10
I don't use FF at ALL & wld like to remove it. The last time I did, however, my [COLOR="Purple"]Chromium[/COLOR] had "issues" w/ bookmarks & passwords. I "lost" both.

Is there a way to remove it w/out causing a prob?

---

### Post by mnemanic on 2012-01-12
> **lovinglinux said:**
> To avoid issues with web sites that doesn't recognize your browser, use [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/59/").


Dear Sir/Madam,

Thanks for your advice but it doesn't help me.

I cannot use User Agent Switcher for any of the cases that I mentioned. In the case of the webpage, it has nothing to to with the page declining my browser version, it is some technical issue due to which an alert shows everytime I click a link, saying "you have chosen to open ....aspx", instead of opening the link. I was in touch with the webpage support and they say it is an error in Ubuntu/Firefox 8.

In the other case, in order to identify myself online I need to donload a special program through my bank. If I use User Agent Switcher to fool the system that I am using Internet Explorer, then it will give me a .exe version of the program, which I then cannot install on my system.

---

### Post by Nopposan on 2012-02-06
I also have an issue with the new Firefox as my Zotero literature citation manager plugin is not yet working (is incompatible) with the new version of Firefox.

Therefore I downgraded via Synaptic and I've also just learned how to "lock version" using the Synaptic package manager as well. 'Could be very useful in the future for all sorts of things, or maybe not, but I'm going to share the mojo with you.

Open Synaptic package manager.

Search for the Firefox package and highlight it.

Downgrade, if you haven't already, by clicking on Package --> Force Version --> <select the version you want>

Then "Apply Changes" and approve of the changes being applied.

Then -- and you might be able to do this beforehand, but I'm not sure -- highlight the "firefox" package again and go to Package --> Lock Version. That is, check the box to lock the version. You may also need to click on "Apply Changes."

Voila! No more annoying prompts to update Firefox to the latest version.

Regarding security updates, however, I think we're SOL. The only thing we can do, so far as I know, is wait for our beloved plugins to catch up with a newer version of Firefox.

'Hope this has helped.

Cheers.

---

### Post by gsoundsgood on 2012-02-06
thanks @Nopposan. 
I had exactly the same problem with Zotero, and solved this issue by downgrading as described in your post... thanks!

---

### Post by Drewvt on 2012-02-08
> **gsoundsgood said:**
> thanks @Nopposan. 
I had exactly the same problem with Zotero, and solved this issue by downgrading as described in your post... thanks!

The citation manager plugin is one thing, I can't speak for that, but for those people who experience Zotero (the main add-on itself) crashes in 10, downgrading is not the best option. The better solution is to switch to the official Mozilla build of Firefox 10 using the [Ubuntuzilla]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page") project.

The advantage of this is that 
1) it allows you to use Zotero 3. If you do a pinned downgrade you will be forever stuck on version 2, because 3 is never coming to Firefox 9, as far as I know.
2) more importantly you get security updates for Firefox this way.

---

### Post by themiddaysun on 2012-07-18
Thank you Nopposan, that is exactly what I needed.  My corporate vpn pluging struggles with the new versions.  This allowed me to lock in the version that I have the most success.:popcorn:

---

