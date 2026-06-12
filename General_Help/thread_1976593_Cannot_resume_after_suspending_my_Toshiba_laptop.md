---
title: "Cannot resume after suspending my Toshiba laptop"
date: 2012-05-09
forum: General Help
---

### Post by Zachary123 on 2012-05-09
I have a Toshiba Satellite with 12.04 LTS installed. 

I can successfully go into Suspend mode but when I attempt to resume, the computer will just go to a blank screen. No buttons I have pressed will resume it so I am forced to hold down the power button and then restart the laptop.

When I had earlier versions of Ubuntu (11.10, and 11.04), resuming the laptop after Suspending it worked fine. 

Can anyone recommend a fix to this problem?

Thanks

-Z

---

### Post by 2F4U on 2012-05-09
Please provide more information about your hardware. There are files pm-suspend.log and pm-powersave.log in /var/log. The file pm-suspend.log is a log file dedicated to what happens during suspend/resume.

---

### Post by Zachary123 on 2012-05-10
Thanks for replying.

Should I just post the results after entering 'sudo lshw' into the terminal?

My first attempt in solving the problem is thinking that it may be my graphics card. I have an ATI Mobility Radeon HD 4570 and I haven't activated the proprietary driver since installing 12.04 LTS. 

When I try to activate the driver it tells me that there was a problem and to look at '/var/log/jockey.log'. I don't really understand what anything in there means though. Could this be the problem?

Thanks,

Z

---

### Post by Zachary123 on 2012-05-11
Problem solved. Although I have no clue how. I think one of Ubuntu's updates fixed a problem and this time I was able to activate the ATI/AMD Proprietary FGLRX Driver. Once activated I restarted the laptop and the suspend/resume function seems to work flawlessly now.

---

### Post by MarjaE on 2012-05-12
I'm having the same problem on 11.04 on an old Vaio. It started immediately after the last kernel update.

---

