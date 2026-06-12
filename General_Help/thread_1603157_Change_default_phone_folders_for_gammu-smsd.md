---
title: "Change default phone folders for gammu-smsd"
date: 2010-10-22
forum: General Help
---

### Post by Neremor on 2010-10-22
Hello!

I'm using gammu-smsd to synchronize my Sony Ericsson K700i with a local folder on my computer. Inbox SMS are saved in /home/username/.smsd/inbox, sms waiting or transmission are saved in /home/username/.smsd/outbox and sent sms are saved in /home/username/.smsd/sentsms... This is how it should work. But it currently only works with inbox sms. All sms on the "Inbox" folder on my cellphone are saved in the local folder and are afterwards deleted on the cellphone. SMS I've sent on my cellphone are saved in the folder "Sent" on it, but are not synchronized with /home/username/.smsd/sentsms for any reason.

A similar problem occured when using the same cellphone with wammu, which is also based on gammu and could therefore be the same problem: It detected the sim-sent-folder as the cellphone-sent-folder and saved all outgoing messages on the sim-card if you didn't change the "Save To" fild to another folder on sms-writing.

In my opinion the two sent-folders on the cellphone are detected wrong. It detects folder 2 as cellphone-sent, but it's the sim-sent location, and folder 4, which is detected as sim-sent, should be cellphone-sent. Is there a way to tell gammu to use cellphone-folder 4 as default sent-folder and not folder 2?

Thanks in advance and greeting!

---

### Post by Neremor on 2010-11-14
I'm just wondering if someone is now knowing the solution for this problem :)

Thanks in advance!

---

