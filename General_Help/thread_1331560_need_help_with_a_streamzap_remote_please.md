---
title: "need help with a streamzap remote please"
date: 2009-11-19
forum: General Help
---

### Post by rbtprkr on 2009-11-19
hi, I am running a mythbuntu 8.1 frontend only machine and have a streamzap remote that works well but the power button does nothing. In my efforts to get the button to work I have run "sudo chmod +s /sbin/shutdown" which made running "shutdown -h now" in a terminal work without asking for a password, so I ran "nano ~/.lirc/terminal"  and in that file I put:

begin
    remote = Streamzap_PC_Remote
    prog = terminal
    button = POWER
    config = shutdown -h now
    repeat = 0
    delay = 0
end

I was hoping this would work because I have other buttons mapped in the mythtv folder but the remote still does squat when the power button is pressed can anyone offer any advice?

---

