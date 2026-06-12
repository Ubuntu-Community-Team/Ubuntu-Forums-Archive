---
title: "Can Nautilus and OO sort files in &quot;natural&quot; order?"
date: 2009-11-03
forum: General Help
---

### Post by runbei on 2009-11-03
Is there a way to set Nautilus and OpenOffice to sort files alphabetically without distinguishing between initial caps and lowercase? Like this -

NOT this:

Alpha
Beta
alpha
beta

But LIKE this:

Alpha
alpha
Beta
beta

Much quicker to find files in long listings like that. (It's how Winblows does it.)

---

### Post by dcstar on 2009-11-03
> **runbei said:**
> Is there a way to set Nautilus and OpenOffice to sort files alphabetically without distinguishing between initial caps and lowercase? Like this -

NOT this:

Alpha
Beta
alpha
beta

But LIKE this:

Alpha
alpha
Beta
beta

Much quicker to find files in long listings like that. (It's how Winblows does it.)

Windows has case-insensitive file names, Linux does not.

---

### Post by Pro-reason on 2009-11-03
> **dcstar said:**
> Windows has case-insensitive file names, Linux does not.
He didn’t ask about case-sensitivity at the system level.  He asked whether Nautilus was capable of ignoring case.

Runbei, I've just looked at my own files in Nautilus, and case is ignored.  I am rather puzzled that you are reporting different behaviour.  I don’t remember any special tweaking to make it work like this.

What version of Ubuntu are you using?

---

### Post by edogd on 2010-08-06
For nautilus:

Put the following in your .cshrc for csh: ```
setenv LC_ALL en_US.utf8
```

or in your .profile for Bash: ```
export LC_ALL=en_US.utf8
```
Then restart you gnome session.
Type ```
locale -a
``` to get a listing.

Also see: [http://ubuntuforums.org/showthread.php?t=614593]("http://ubuntuforums.org/showthread.php?t=614593")

---

### Post by runbei on 2010-08-06
Thanks, edogd. Fortunately, I don't have to go to such lengths, as I recently upgraded to Mint 9 and Nautilus sorts in natural order (as it did formerly before it mysteriously stopped doing so). Nor do I have to figure out where my ".cshrc for csh" is. ?-)

---

