---
title: "Problem emptying trash in Evolution Mail"
date: 2010-07-09
forum: General Help
---

### Post by Iamwrongagain on 2010-07-09
I am 61 years old and brand new to Ubuntu. My son built a computer for me which I am using. I hated Windows so he installed Ubuntu 9.10 which I love. by my son left for the Air Force Acdemy and when he left he told me and I was on my own so I am doing my best to learn. Everything was going fine but today I encountered a problem. When I tried to empty my trash in the Evolution Mail program, I encountered this error message:

[COLOR=Red]Error while Expunging folder.

Error storing '~/.evolution/mail/local/Sent (mbox)': Summary and folder mismatch, even after a sync[/COLOR]

I googled the error and found this solution:

[COLOR=Red]Problem solved.  I finally found the solution in another thread. I first used Evolution File > Backup Settings.

Then I went to my .evolution/mail/local and deleted all files that had an extension of:
.index
.cmeta
but NOT .data

When restarted it takes a few minutes to rebuild. Then I was able to successfully delete everything in my trash folder.[/COLOR]   

Here is my problem and I feel like an idiot. I have looked and looked and I cannot find the .evolution/mail/local folder. Could some one tell me in a step by step fashion how to get to it. Or perhaps am I using the wrong corrective action. If that is the case, then what shouldl I do. Many thanks.

Jim

---

### Post by plucky on 2010-07-09
Open **Places > Home Folder** and  then navigate to **View** and click on **Show Hidden Files** and all the hidden files in your home folder should now be visible in the window.You can now see .evolution folder,use that to navigate to where you want.

Good Luck

---

### Post by cavalier911 on 2010-07-09
System files and folders with a period in front, often refered to as dot files are hidden by default. Ctrl+h,or View/Show hidden files in menu of nautilus file manager,terminal ls -a to see them.Cuts down on the clutter in your home folder.

Rather than delete files and folders,add .bkup to them or make a folder and put them in there.The system doesn't see them and in effect you've removed them.Just in case whatever you try doesn't fix things and breaks something else.You still have the old files to restore.

---

### Post by claracc on 2010-07-09
> **Iamwrongagain said:**
> . When I tried to empty my trash in the Evolution Mail program, I encountered this error message:

[COLOR=Red]Error while Expunging folder.

Error storing '~/.evolution/mail/local/Sent (mbox)': Summary and folder mismatch, even after a sync[/COLOR]

Here is my problem and I feel like an idiot. I have looked and looked and I cannot find the .evolution/mail/local folder. Could some one tell me in a step by step fashion how to get to it. Or perhaps am I using the wrong corrective action. If that is the case, then what shouldl I do. Many thanks.

Jim

This is acommon problem with evolution when you try to delete the mails in the trash basket.

To fix it, I do other thing, you go to places -->personal folder, mark on see --> hidden files, go to .evolution --> mail --> local. There is a folder named folder.db
Close evolution, delete folder.db (or change its name to .old). Then run evolution and try to empty the trash folder. This time it will work.

---

### Post by Iamwrongagain on 2010-07-09
My sincere thanks to Mr.(Ms) Plucky, Mr.(ms) Cavalier911, and Mr. (Ms) Claracc for their rapid on-the-mark-responses to my problem. When I get off work tonight I will give them a  try and let you all know how it came out. But thank you all for sharing your time and knowledge.

Jim

---

### Post by Iamwrongagain on 2010-07-11
It worked like a charm. i am back in business. Thanl you all.

Jim

---

