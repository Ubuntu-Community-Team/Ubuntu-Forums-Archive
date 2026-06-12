---
title: "All instances of shell not working. Maybe hacked?"
date: 2010-08-14
forum: General Help
---

### Post by brianvan on 2010-08-14
I have a serious problem with my Ubuntu installation (in a VM). In virtually every case where I try to access the command-line (Terminal, logging in directly into shell), I am not getting the command line. I get a blank line, and anything I type in results in the following text being replied:

"WinSCP: this is end-of-file:0"

I know what WinSCP is, and I'm not using it at all. And the result is that I can't run any command-line programs or commands anywhere within the VM anymore.

Both the VM and the host computer have been rebooted multiple times. I actually hadn't edited anything in the VM in a while, and I came across this issue while needing to fix another issue...

Somehow I'd been locked out of my OpenSSH access on the host computer (Windows Vista), and while troubleshooting that, I found that someone was trying to hack into SSH with random password attacks. I haven't noticed any suspicious activity otherwise (no missing files, no malicious programs, no traces of a hacker) but after looking at the logs on the Ubuntu VM, it looks as if someone was trying to get into that computer as well. The only fishy thing I've noticed is the command-line shell issue on the VM.

So, now that I've turned off SSH and I'm trying to get Ubuntu fixed... what can I do? Did some hacker get into the Ubuntu VM and set up a shell redirect or something? Or is this a more innocent or easily fixed issue?

---

### Post by brianvan on 2010-08-15
Update:

I'd kinda found the shell problem, somehow scp-only was installed and replacing my shell.

I'm still unsure if this is something I should be worried about, since I didn't try to install that myself. My firewall + disabled SSHD are keeping the script kiddies out, for now, but I'm still very concerned about that...

---

