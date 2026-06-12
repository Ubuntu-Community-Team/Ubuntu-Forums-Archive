---
title: "SMBus not enabled"
date: 2011-06-04
forum: General Help
---

### Post by mastablasta on 2011-06-04
What does the message spilled out on start means

It says something like

SMBus not enabled. Upgrade BIOS or use force=1.

i can't upgrade bios. So what does the message mean and how do i use force=1 ? where do i put this command?

---

### Post by mastablasta on 2011-06-07
bump

---

### Post by mastablasta on 2011-06-22
BUMP no 2!!!

---

### Post by mastablasta on 2011-06-27
Number 3. still unsolved.

---

### Post by xollicle on 2011-06-29
I get the same thing on my TTX v7000 1ghz laptop on debian squeeze.

Also see this:
[http://www.kernel.org/doc/Documentation/i2c/busses/i2c-piix4]("http://www.kernel.org/doc/Documentation/i2c/busses/i2c-piix4")

To use force=1 you would have to use the computer as a completely experimental machine for months before you could consider it stable enough for work. Just leaving it the way it is would be best. The only things you are missing out on are SMBus stuff like cpu temperature, fan speeds and things like that I believe. That's all the help I'm giving you.

---

### Post by mastablasta on 2011-06-30
thanks at least something. i thought it has to do something with the baterry monitor. 
system otherwise works just fine. even gkrelm is showing some data. so i guess the warning is not that important.

---

