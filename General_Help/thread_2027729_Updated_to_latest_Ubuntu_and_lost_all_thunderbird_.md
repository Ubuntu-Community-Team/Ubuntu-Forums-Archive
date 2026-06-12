---
title: "Updated to latest Ubuntu and lost all thunderbird emails"
date: 2012-07-16
forum: General Help
---

### Post by greeniekin on 2012-07-16
My mother has had ubuntu installed on her laptop and the version was from 2010 or something and had been asking her to update for a long time. I eventually got around there and did it for her.

Though now Thunderbird no longer has her emails.

While I suspect they are lost and nothing can be done I am praying that there is some way to recover those emails.

Also it was not  afresh install it was an update using the update updated thing.

I appreciate any help you can give.

---

### Post by OM55 on 2012-07-16
It is very possible that your emails and settings are still there but simply not defined anymore in the new Thunderbird installation.

Both your old and new Thunderbird installation keep all the data files (emails and settings) under your home folder in a hidden directory named ".thuderbird":

1. Open Nautilus (if you don't know how, you can also open a terminal and type 'nautilus' ) and navigate to "Home Folder". hit CTRL-H and you will suddenly see additional files all file names starting with a "." that were previously hidden. Double click on ".thunderbird".

2. The next folder in the tree would be a profile name, which is a collection of letters and numbers (different for each installation). Click on that folder and you should see several files and folders. The typical setting is that email account is also the top folder name where all the emails are. If you see something familiar, double click on that one.

3. Now you should see several files, including "inbox", "sent" and any custom emailbox created. All emails in a specific emailbox are in that one single file.
If you see familiar emailbox names that also have size in megabytes (can't tell how much, it is directly related to the combined size of the email messages inside) - here are your lost emails.

if by now you found the lost email files, this is the first step. If no files are found (and you can't find something familiar anywhere under the ".thunderbird" folder, you may be out of luck..

So lets start with this first step to determine if the files are there - and post here the results. 
If the files are indeed there, I will follow up with instructions on how to restore the emails.

---
And last but absolutely not least - there is nothing like a life lesson to learn to appreciate the value of a timely backup!
Before you are doing any change to the system that (as you see) could cause you a loss of data, estimate how much time and money you would be willing to spend/pay in order to retrieve your lost data - should that happen in the process. That is the same amount of money and time you should feel comfortable in putting into making your backup beforehand!

---

### Post by greeniekin on 2012-07-20
Sorry for the delay I only now just visited my parents.
In the thunderbird folder there is a directory called "a7nzttjl.default" and another called "crash report".
She remade an email account to get her email in the mean time. So there being only one folder suggests it is for the new account not the old one.

She had kept pretty much every email for the past 2 years and the "a7nzttjl.default" folder is only 33.6 mb.

Which I imagine would be rather small even if all here emails do not contain attachments.

---

### Post by ryanepod on 2012-07-20
Depending on if its iMAP or POP3 they could still be on the server's web site for example all my email in KMail also gets backed up at Gmail

---

### Post by greeniekin on 2012-07-22
She was using pop3 previously. So I do not think it is stored on the server. Thank you everyone for all your advice.

---

