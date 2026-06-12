---
title: "How do I make Seamonkey default for opening urls?"
date: 2011-10-07
forum: General Help
---

### Post by pretty_whistle on 2011-10-07
I already made it default for opening html files-I did it this way:

> I right-clicked an html file and chose to open it with another  application.  I also made sure it was checked to "Remember this  application to open html files".

I don't know how to make it open urls though.  How do I do that?

I have Ubuntu 11.04.

---

### Post by pqwoerituytrueiwoq on 2011-10-07
search for "Preferred Applications" in the unity application search
in classic (gnome 2)
system->preferences->Preferred Applications

---

### Post by pretty_whistle on 2011-10-07
> **pqwoerituytrueiwoq said:**
> search for "Preferred Applications" in the unity application search
in classic (gnome 2)
system->preferences->Preferred Applications

It's not letting me change it.

---

### Post by pretty_whistle on 2011-10-07
It has Chromium as default so I thought if I uninstalled it it would force it to recognize Seamonkey.  It didn't.  Instead it reinstalled Firefox behind my back - I took that out long ago.  Then I tried uninstalling Firefox again and it installed Chromium behind my back!  WTF is that about?

I'm getting stuck with one of these 2 programs but I want neither and it won't quit doing it.

WEIRD.

---

### Post by pqwoerituytrueiwoq on 2011-10-07
try the custom setting then or use chrome to make itself the default browser

---

### Post by pretty_whistle on 2011-10-07
> **pqwoerituytrueiwoq said:**
> try the custom setting then or use chrome to make itself the default browser

For the browser it doesn't show a custom setting.

---

### Post by pretty_whistle on 2011-10-07
Guess there's no solution to this.  :(

---

### Post by Krytarik on 2011-10-07
I presume you 'installed' Seamonkey manually, right?
If so, why don't you just install it from the official repos - via Software Center, Synaptic, or apt-get!?
This way you could also choose it in "Preferred Applications".

And I've never heard of something like this, nor do I believe it, sorry:
> **pretty_whistle said:**
> It has Chromium as default so I thought if I uninstalled it it would force it to recognize Seamonkey.  It didn't.  Instead it reinstalled Firefox behind my back - I took that out long ago.  Then I tried uninstalling Firefox again and it installed Chromium behind my back!
Regards.

---

### Post by pretty_whistle on 2011-10-07
> **Krytarik said:**
> I presume you 'installed' Seamonkey manually, right?
If so, why don't you just install it from the official repos - via Software Center, Synaptic, or apt-get!?
This way you could also choose it in "Preferred Applications".

And I've never heard of something like this, nor do I believe it, sorry:

Regards.

I had installed Seamonkey manually a few weeks ago.  Since this problem came up I decided to get it through Software Center and delete the manually installed one.

That done I decided to remove Chromium while I was at it.

Then I checked Preferred Applications and I found Firefox there and still no option for Seamonkey.

That I found weird so I thought, "Maybe if Firefox wasn't installed it would make Seamonkey be recognized."  It didn't.  Instead it reinstalled Chromium and still no Seamonkey recognized.

Just explaining what's going on.  I understand you don't believe it, that's fine-then just leave it at my inability to get Seamonkey as default.

Edit:  When Firefefox and Chromium are both installed from Software Center it only allows one browser, meaning I can't unchoose it and choose the other one.

---

### Post by pretty_whistle on 2011-10-07
I think my not removing the Seamonkey manual install BEFORE trying it from Software Center has produced this issue.  I'll do it correctly this time and see what happens.

---

### Post by pretty_whistle on 2011-10-07
Update:

I tried the above-failed.  But I did have Seamonkey crash twice.  I'm removing it and going with a manual install of Seamonkey.

Also Chromium and Firefox came with Ubuntu 11.04 and because of it I have to have at least one installed.  This is a weird way to make it.  Whatever-it's still better than Windows so I'm keeping it.

:o

---

### Post by Krytarik on 2011-10-07
> **pretty_whistle said:**
> I tried the above-failed.  But I did have Seamonkey crash twice.  I'm removing it and going with a manual install of Seamonkey.
Ok, then have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1853791](http://ubuntuforums.org/showthread.php?t=1853791)

> **pretty_whistle said:**
> Also Chromium and Firefox came with Ubuntu 11.04 and because of it I have to have at least one installed.  This is a weird way to make it.  Whatever-it's still better than Windows so I'm keeping it.
In fact, you could remove both of those, as they are no "dependencies" of the meta-package "[ubuntu-desktop]("http://packages.ubuntu.com/natty/ubuntu-desktop")", only Firefox is a "recommend" of it. And a mechanism you are describing is simply impossible, even if they were "dependencies"; in that case, they would instead tear "ubuntu-desktop" with them.

---

### Post by pretty_whistle on 2011-10-07
> **Krytarik said:**
> Ok, then have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1853791](http://ubuntuforums.org/showthread.php?t=1853791)


In fact, you could remove both of those, as they are no "dependencies" of the meta-package "[ubuntu-desktop]("http://packages.ubuntu.com/natty/ubuntu-desktop")", only Firefox is a "recommend" of it. And a mechanism you are describing is simply impossible, even if they were "dependencies"; in that case, they would instead tear "ubuntu-desktop" with them.

Interesting....a bug.  I believe it.

Plus the issue, which may be related, of insisting I have Firefox or Chromium installed but can't remove both.  Per this issue, I've figured "If you cant beat em, join em" so I choose Chromium as my browser since it's insisting I have one or the other installed and Seamonkey wasn't recognized and crashed anyway.  I find it easier than a manual install of Seamonkey.

---

### Post by vnce on 2011-10-12
@pretty_whistle: I experienced the frequent crashes of Seamonkey. It is an existing bug, which is still unresolved. It comes from an incompatibility between the spell checker and Seamonkey. Deactivating spell checking by edit->preferences

- Browser->Languages->Spelling: When typing check my spelling: never
- Mail & Newsgroups->Composition->Spelling: disabling both boxes

did the job for me. It now runs stable since then.


Back to the initial question: I have no manual installation of seamonkey. Only the standard way. However Seamonkey does never appear in the choice lists of neither "Web Browser" nor "Mail Reader" in the Preferred Applications window. Even after uninstalling firefox and evolution etc. Chromium is automatically installed and the only choice in the Browser list, while KMailService could not be removed at all. Any idea, how to get Seamonkey into that lists, without "brute force" risking future updates restoring my manual changes ;) ?

---

