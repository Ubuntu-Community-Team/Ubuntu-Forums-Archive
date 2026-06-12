---
title: "xterm sometimes doesn't display text"
date: 2012-07-24
forum: General Help
---

### Post by ArlieS on 2012-07-24
I have a desktop with ubuntu 12.04 LTS workstation, purchased pre-installed from System76. I've added some additional software myself, and done "apt-get update" and "apt-get upgrade", but it's still pretty close to virgin. (I unpacked it 3 days ago.) 

I'm using a lot of xterm windows for everything from mail to system administration. And rather frequently, but not according to any pattern I can figure out, a big chunk of text fails to display.  (Not normally the whole window, but usually several lines.) The ctrl-L key has always fixed the situation - at least until it happens again.  I have no display problems in any other windows - emacs, firefox, and the various GUI-style tools that come with the workstation installation all appear to display everything properly.

As you can imagine, this is very inconvenient. Is it a known bug? Is there a workaround? Would downgrading my xterm version help? Changing the TERM value?

Thanks for any help anyone can give me,

---

### Post by itcotbtoemik on 2012-07-25
> **ArlieS said:**
> I'm using a lot of xterm windows for everything from mail to system administration. And rather frequently, but not according to any pattern I can figure out, a big chunk of text fails to display.  (Not normally the whole window, but usually several lines.) The ctrl-L key has always fixed the situation - at least until it happens again.  I have no display problems in any other windows - emacs, firefox, and the various GUI-style tools that come with the workstation installation all appear to display everything properly.

The usual reason for display problems in Ubuntu is the buggy compiz feature that they've been providing for the past 3-4 years.  (Sometimes this affects emacs as well - perhaps it's "improved").   The corresponding workaround is to turn that off.

---

