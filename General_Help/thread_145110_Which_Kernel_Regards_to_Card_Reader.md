---
title: "Which Kernel? Regards to Card Reader"
date: 2006-03-15
forum: General Help
---

### Post by dpaint4 on 2006-03-15
I'm looking forward to support for my laptop's internal 6-in-1 card reader by Texas Instruments. I read a thread from four weeks ago where an admin told someone else with the same issue that it would probably be functual after kernel 2.6.15.

Is there a Terminal command or someplace I can look to see which kernel I've got? I know that it just updated a couple days ago through the automated update system, and I'm sure  it's not at 2.6.15 yet, but I'd like to know how far off that is just to satisfy my own stupid eagerness.

Is that something that will be associated with Dapper? Breezy is my first Ubuntu.

K. That's it. Anyone have any additional info on the support for internal card readers or know how to view their kernel version?

Can't view the System Log under System Tools. It reliably crashes as soon as I start it.

---

### Post by dpaint4 on 2006-03-15
I'm a little embarrassed that as soon as I post to a topic it dies, and when I ask a question no one ever replies. I swear. I'm an okay guy.

I'm like the topic grim reaper or something.

---

### Post by dschaller on 2006-03-29
To check what kernel is running, give the command "uname -rsv" at the terminal prompt.

I have a Mitsumi card reader/floppy drive combo that works fine in Ubuntu breezy. Automounts, autodetects, etc. My impression has been that USB mass storage is actually pretty well supported, but I don't know much about built-in laptop devices like the one you have.

---

