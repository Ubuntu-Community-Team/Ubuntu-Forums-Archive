---
title: "Ubuntu 10.04 64bit crashes"
date: 2011-10-07
forum: General Help
---

### Post by pelv13 on 2011-10-07
Hey there, and thanks for your help =).

I have a Sony VAIO Laptop (vpcf126fm). 

processor Intel Core i7 cpu     q740 @1.73Ghz 1.73 GHz
6.00 GB installed ram

Anyhow, my system comes with Windows 7 Home Premium installed, and I recently installed the Ubuntu 10.04 OS to dual boot with that. The trouble is that Linux crashes randomly with disturbing frequency. I have considered switching to the 32bit version to resolve this issue, but I have not done so yet. I can think of no specific trigger for this problem (i.e. , running a particular program), though crashes are more frequent when I am using Firefox and the Ubuntu Software Centre. When the system crashes my mouse cursor will move (but cannot click) and the keyboard seems incapable of input of any kind. The screen does not go black, nor is an error message of any kind generated.

I have had no experience with Linux prior to this installation, and my understanding of computers in general is very limited. I can provide any other info upon request, though it may help if you provide the procedure for gathering it.

I am curious if this problem is common. If so, is there a thread all ready dedicated to this that I was unable to find? If it is not common, what options should I be considering? I look forward to hearing from you! =)

Thanks for sharing your valuable time with me,
Miles

---

### Post by 2F4U on 2011-10-07
Can you provide information about your graphics card and what driver you use? Also, it could be helpful if you look into the log files (/var/log/messages) after a crash.

---

### Post by pelv13 on 2011-10-07
NVIDIA GeForce GT 330M... I will try running it now, and provide the log as soon as it crashes.

---

### Post by pelv13 on 2011-10-17
it's really funny... i waited hours for it to crash after my last post... it crashed twice both right after boot this morning... anyhow, here it is   Oct 17 07:29:43 Sky-Net rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="754" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'. Oct 17 07:30:01 Sky-Net CRON[2296]: (root) CMD (start -q anacron || :) Oct 17 07:30:01 Sky-Net CRON[2295]: (CRON) info (No MTA installed, discarding output) Oct 17 07:30:02 Sky-Net anacron[985]: Job `cron.daily' terminated Oct 17 07:30:02 Sky-Net anacron[985]: Job `cron.monthly' started Oct 17 07:30:02 Sky-Net anacron[985]: Job `cron.monthly' terminated Oct 17 07:30:02 Sky-Net anacron[985]: Normal exit (2 jobs run) Oct 17 07:30:02 Sky-Net anacron[2327]: Updated timestamp for job `cron.monthly' to 2011-10-17 Oct 17 07:31:36 Sky-Net kernel: [ 1242.480219] CE: hpet6 increased min_delta_ns to 7500 nsec Oct 17 07:31:36 Sky-Net kernel: [ 1242.480229] CE: hpet6 increased min_delta_ns to 11250 nsec Oct 17 07:32:59 Sky-Net sudo: pam_sm_authenticate: Called Oct 17 07:32:59 Sky-Net sudo: pam_sm_authenticate: username = [pelv13] Oct 17 07:32:59 Sky-Net sudo: pam_sm_authenticate: /home/pelv13 is already mounted

---

### Post by pelv13 on 2011-10-24
i am unsure how to check my drivers in linux... i was here reading all of this again to make sure i didn't miss anything important... i spent about a half hour on a search engine looking for information that was relevant to that, but it made little sense to me...

i will be doing further research to see if i can learn how to find information about the drivers... this post is meant to "bump" this thread as much as it is to recieve information in this regard... if i do find information about my linux drivers i will be sure to post them also...

---

