---
title: "Chromium won't stop suggesting URLs, even though I've told it to stop"
date: 2011-01-17
forum: General Help
---

### Post by t0p on 2011-01-17
I'm using Lubuntu on my netbook, and its default browser Chromium.  Whenever I'm typing an URL into the address bar, Chromium suggest possible URLs based on what I've typed in... even though I don't want it to!

Under Preferences > Under the Bonnet is an entry **Use a prediction service to help complete searches and URLs typed in the address bar**.  I have unchecked this option, but Chromium still keeps on suggesting URLs.  Which means Chromium is remembering my browsing history whether I want it to or not.  It still happens even after I've clicked the "Clear browsing history" button.

This behaviour is still there when I open an "Incognito" window, which is *really* disturbing.  Because Chromium says "Incognito" browsing is secure and private when clearly this is not so.

Is this a bug/"feature" that I must put up with if I want to use Chromium"?  Or am I missing a setting somewhere that will stop this behaviour?

---

### Post by t0p on 2011-01-19
bump

---

### Post by t0p on 2011-01-19
bump

---

### Post by t0p on 2011-01-19
bump

---

### Post by t0p on 2011-01-19
A little bump.  I hope I can find out how to fix this, otherwise I may have to switch to Firefox on my Lubuntu box (better the devil you know etc).  So, what do you reckon?  Can you tell me how yto sort this problem?  It's a tad annoying; and, even though I don't really do anything on the net thast I'm *ashamed* of, I still value my privacy.  I realise that **Chrome** is a Google product, and that Google have a vested interested in knowing what we're all up to - but **Chromium** is a Free version of the browser, and I figured its devs would have done something about this.

Any suggestions?  Or must I remove Chromium and install Firefox? I use Lubuntu on my netbook because of its relative lightness - installing the allegedly-bloated Firefox thus seems a step backwards.  But if there's nothing else for it...

Help, anyone?  Cheers!

---

### Post by SteveDee on 2011-01-19
> **t0p said:**
> ...Or must I remove Chromium and install Firefox? I use Lubuntu on my netbook because of its relative lightness - installing the allegedly-bloated Firefox thus seems a step backwards...


I don't believe that Chromium is lighter than Firefox: [http://ubuntuforums.org/showthread.php?t=1657610](http://ubuntuforums.org/showthread.php?t=1657610)

---

### Post by t0p on 2011-01-19
> **SteveDee said:**
> I don't believe that Chromium is lighter than Firefox: [http://ubuntuforums.org/showthread.php?t=1657610](http://ubuntuforums.org/showthread.php?t=1657610)

Interesting... so maybe I should just remove Chromium and replace it with Firefox...

Yes, I think that's what I'm going to do.  Goodbye Chromium!  At least I know Firefox does what I want it to do, without having to grapple with an unfamiliar interface.

---

### Post by t0p on 2011-01-20
Right, I've installed Firefox on my Lubuntu-running netbook, and all seems fine right now.  It's quite nice to have reverted to the familiar old interface, after grappling with Chromium.

I haven't removed Chromium yet.  Hedging my bets I suppose.  But its day will come, I think.

One wee problem.  Before I installed Firefox, I made a back-up of my Chromium bookmarks.  I'd had no problems importing Firefox bookmarks to Chromium, so I figured I'd be able to import the Chromium bookmarks to Firefox.  So, I made a back-up of my bookmarks, entitled deimos-bookmarks-2011-01-20.  Now I've installed Firefox, it's reverted to the bookmarks it had back on 3 Jan 2011.  I've tried importing deimos-bookmarks-2011-01-20, but it comes back as "unsupported filetype"... even though under Properties it's described as "File type: Mozilla bookmarks" and I've changed the "Open With" option to "Firefox Web Browser".

Anyone know how I can get my new Firefox browser to accept this bookmarks file?  I really don't fancy messing round manually adding all the changes that I did to the bookmarks while in Chromium...

---

### Post by t0p on 2011-01-21
Ignore my rant about importing Chromium bookmarks into Firefox.  I was wrong.  (Wow, it feels weird typing "I was wrong", as I am right nearly all the time.

What I hadn't noticed, in my hast and wrath, was that the Chromium bookmarks had been *appended* to the FF bookmarks.  I hadn't expected that, as importing FF bookmarks usually results in the new bookmarks replacing the old.  That's a Chromium feature I really would like to see adopted by FF.  Would I contact Mozilla about this, or post a bug in Launchpad, or both?  Or neither?  Or should I do both, and other stuff?  Hopefully a FF dev is reading this, and I won't have to do anything?!

Okay, so now I have moved from Chromium to FF on my Lubuntu box, and so far its been all good.  Probably because 3 or 4 years' almost-exclusive FF use has got me used to it.

Will doing a 

[code[sudo apt-get purge chromium-browser
[/code]

be okay now?  Or will purging chromium-browser take away stuff that I need for other stuff?  Or is Lubuntu clever enough to remove only what isn't needed? (I don't usually ask questions like that, but with Chromium and Lubuntu itself being rather beta-ish, I figured M may as well ask before borking my box...)

---

### Post by SteveDee on 2011-01-21
> **t0p said:**
> 
...Will doing a 

[code[sudo apt-get purge chromium-browser
[/code]

be okay now?...

I'd use Synaptic, and mark Chromium for complete removal. That way, if you have a problem, you can use Synaptic menu File > History to selectively add back in any packages that you shouldn't have removed.

---

### Post by t0p on 2011-01-26
Thanks.

---

