---
title: "Public Linux Terminals - Linux In The Wild"
date: 2010-07-07
forum: General Help
---

### Post by Adler on 2010-07-07
Hi All,

I'd like to move one of the Linux computers that I work with into a hotel business center. M$ has too many issues - updates, scanning for virii, removing adware, malware, defragging the HDD, etc. > Oh, they say this computer is sooo slow.

Well, we have all been there and done that. That is why we all moved to Linux. 

I'd like to move the system that I have into the Public Venue and be sure to limit what can be done in the hands of hotel guests. Sort of Publc Library M$ scenario, but with a few Linux open source user options.

I have an idea what I need that hotel guests should be able to do. Anybody introduced *Linux In The Wild.*

Thanks in advance for any comments.

Best Regards,

JJMacey
Tempe, Arizona

---

### Post by Revolutionary101 on 2010-07-07
Are you going to have an individual account for each user? 

I was thinking you could have two accounts on the computer. One would be yours (administrator) and then for the hotel guests. You would have the computer automatically log into the non-administrator account when the computer is turned on. Then as long as they don't know the password to the administrator account, they can't modify any of the programs or system settings.

---

### Post by Adler on 2010-07-07
Revolutionary101,

Thanks for the quick reply. Personally, I've done that for a few people so that they could use my Linux systems, then they get confused @ the splash screen e.g. How do I log-in? I'd need a simple password like "Guest".

I'd like to auto boot-up a system to the sub-user level, get rid of all possible options other than I have allowed. This way the user might either only see Icons, and most certainly not see a menu with things like Skype or the other apps that we see or use.

Thanks for that quick reply.

Regards,

JJMacey
Tempe, Arizona

---

### Post by Revolutionary101 on 2010-07-07
From what you have said I would recommend doing this:

1. Setup the computer originally with only one user, this account will be the administrator.

2. Once you have the computer all setup go to System>Administration>Users and Groups

3. Create a new user named "Guest"

4. Create a simple password for it and click on the option that says "Don't ask for password on login". This way it will bring you to the login screen at bootup and it will show the Administrator account (which requires a password) and the guest (no password required for login) account. You could just tell the people to click on the Guest account to log in.

5. When you have created the Guest account, you can go under System>Administration>Users and Groups (on the administration account of course) and select the Guest account. When you have done that click on "Advanced Settings" and go to the "User Privileges" tab. Here you will be able to restrict the Guest from doing anything you don't want them to.

I hope that is what you meant by sub-user level. To only get icons on the desktop drag and drop the programs you want from the menu to the desktop. Then to get rid of the menu just right click on the menu (under the Guest account and click "Remove from panel"

I hope it helps!

---

### Post by JK3mp on 2010-07-07
Yep he seems to have it covered, then you can just have a post up or sticky on the desk saying password is guest etc.etc. But be ready for guests to be confused in the new environment of linux, especially if they try to run a native windows app etc.

---

### Post by Adler on 2010-07-08
Guys,

Thanks, I'm off for the next couple of days. And won't see the system that I am talking about for that time.

I'll do a complete re intsall, but need to limit the user to FF (with the codecs for Video/Audio), Adobe Reader, Open Office, and maybe a few others. There is no real need to keep these "guests" on the pc for too long.

You'd be supprised to know what they try to do. Again, I go back to the Public Library concept of offering a few things that are nessecary.

I don't want to let anyone edit / alter a menu. What I allow is allowed.

Thanks for these responses.

Regards,

JJMacey
Tempe, Arizona

---

### Post by Dustin2128 on 2010-07-08
> **Adler said:**
> Hi All,

I'd like to move one of the Linux computers that I work with into a hotel business center. M$ has too many issues - updates, scanning for virii, removing adware, malware, defragging the HDD, etc. 

Well, we have all been there and done that. That is why we all moved to Linux. 

I'd like to move the system that I have into the Public Venue and be sure to limit what can be done in the hands of hotel guests. Sort of Publc Library M$ scenario, but with a few Linux open source user options.

I have an idea what I need that hotel guests should be able to do. Anybody introduced *Linux In The Wild.*

Thanks in advance for any comments.

Best Regards,

JJMacey
Tempe, Arizona

You can easily setup a guest account with no password and limit what guests could do on it. Very good use for linux due to user privilege system (can't do anything harmful to the entire system without super user status). Suppose it depends on what you want them to not be able to do, but I'm sure you could find a tutorial to do almost anything along these lines. Something useful you could do, keep a copy of the /home/guest directory on your account, and every night wipe out the /home/guest directory and replace it with the blank backup. Or write a macro to do it for you.

---

### Post by lavinog on 2010-07-08
If you are concerned about users demanding windows, you could setup xp in a vm.  If they mess it up, restoring to the original state is pretty simple.

Something to think about:  If a hotel was to provide macs for guests to use, how would customers respond?

---

### Post by Adler on 2010-07-08
lavinog,

> If you are concerned about users demanding windowsically, save the 

Dah, what M$ version disk should be @ hand. We are trying to introduce Linux @ public terminals. VMWare is out out of the question. We do not want to network (right now), but want to introduce a safe, effective Linux system that is transparent to the USR. 

Basically, keep a Linux system up that not has to be repaired daily. 

Surly, there is a Public Use of Linux out there.

Thanks for the post.

Regards,

JJMacey
Tempe, Arizona

---

### Post by Adler on 2010-07-08
> If you are concerned about users demanding windows, you could setup xp in a vm. If they mess it up, restoring to the original state is pretty simple.

Hi All.

No M$, No MAC. No VMWare.

Public terminal restricted.

Thanks for those posts.

JJMacey
Yempe, Arixona

---

### Post by Wharf Rat on 2010-07-10
Adler,
While not the same situation as yours, a  couple of years ago I set up a public PC with Ubuntu at my office entry area for public  use.  Same reasons as you posted.  My time was too valuable to chase MS virii.

I think I have had to help only 2 or 3 users in that time frame.  I now have 2 machines set up for employees who pretty much surf and read mail.  NO PROBLEMS. NO COMPLAINTS!

They do not have as many toys as the Windows users.  They cannot access my accounting (Peachtree).  And, they are limited to getting their mail via web interface from our Domino server.  Notes for Linux is nothing more than a frustration.

I have kept the Gnome desktop default settings and every couple of months I check the updates.  Both machines are OLD...and work just fine.

---

### Post by Adler on 2010-07-10
> a couple of years ago I set up a public PC with Ubuntu at my office entry area for public use

Wharf Rat,

Thanks for the reply. I think our circumstances are identical. I'd like to put a Linux Box in a hotel business center, w/o anything M$. What I've done so far is create an "Admin" and "Guest" login on boot w/ the PC that I want to use. I do this normally for friends, and family i.e. separate them from me as Root / SysAdmin. I'll let them do what they want, create their home pages, Facebook set-ups, etc.

However, we are no dealing w/ the public. I want to lock their menu choices down to Firefox, Open Office, and what ever I've not considered, but /usr useful. There should be no menu choices as now exists on the box that I am playing with here. 

As open as Linux is the box that I am talking about needs to be locked down even so far as someone can not change the desktop background. I'll provide the Wallpaper, thank you - LOL.

I think you know what I mean!

Again, thanks for the reply.

Best Regards,

JJMacey

---

### Post by mike555 on 2010-07-10
There is an app that locks the desktop , called;  pessulus  , in the repository.

---

### Post by ram2500 on 2010-07-10
I think that in order to successfully deploy Linux in a hotel business center, using Ubuntu would likely be the best choice:p. Also, set up OpenOffice to save in Microsoft formats by default (.doc, .xls, .ppt), **lock down the system** so that users don't change settings, and prevent access to the terminal. Have the firewall set up properly and consider a content filtering system if a proxy server with filtering capabilities isn't already available. And, I think it would be also advised to have files deleted upon exit (including the cache of Firefox) and preventing files from being saved to the hard drive so that users don't fill up the hard drive. I have no experience setting up hotel business center computers:p but by experience of using them, many were slow, had other people's files all over them, and could easily have settings changed. Many hotels I've stayed at had Windows XP Home (one hotel, A Days Inn, mind you, had Windows 98 and Office 2000 I think) and the account was "Administrator" for guests to use. Thus, the computer was heavily modified to the hundreds of guests' taste.

---

### Post by Adler on 2010-07-10
Guys, 

Thank for those replies.

Let me see how these things work out.

Regards,

JJMacey
Tempe, Arizona

---

