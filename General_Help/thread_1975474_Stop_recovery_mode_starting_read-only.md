---
title: "Stop recovery mode starting read-only"
date: 2012-05-07
forum: General Help
---

### Post by Paddy Landau on 2012-05-07
When I boot into Recovery Mode, it starts in read-only mode. This means that the /home folder is not mounted (it is on a separate partition), and the check-disks option appears to hang.

I know that I can "fix" it as follows, but surely it shouldn't do it in the first place?
```
mount -o remount,rw /
mount /dev/sda5 /home
```How can I fix this?

EDIT: I'm using 12.04 fully updated.

---

### Post by bogan on 2012-05-07
Hi! **Paddy**,

In 11.10 recovery menu there was an option to mount things in Read/Write mode, but in 12.04 it has been dropped.

Selecting the safe Mode Low-Res Graphics, says it will change to Read/Write and asks for confirmation.

But what is even worse, the drop to root terminal option now demands the "Root Password" and will not accept the normal user log-in Password even though it is Admin authorized.

Does that option - if you knew what it expects as a Root Password - perhaps give the same Read/Write permission change?

Chao!, **bogan**.

---

### Post by Paddy Landau on 2012-05-08
Hi bogan,

I don't get a request for the root password -- it is not even supposed to be set. Did you set a root password, perhaps?

When I try to go to low-res graphics, I get exactly the same as when I try to check the disks: it asks to go into read-write mode (which I accept), then it appears to hang. I have to press Ctrl-C to return to the menu.

I think the Recovery Mode is broken and hasn't even been tested.

I shall raise a bug for this.

---

### Post by Paddy Landau on 2012-05-08
I have raised a bug for this.

Please [go there to vote]("https://bugs.launchpad.net/ubuntu/+bug/996454") if you think it affects you (the green wording near the top of the page).

---

### Post by bogan on 2012-05-08
Hi!, **Paddy**,

You Posted :>  I don't get a request for the root password -- it is not even supposed to be set. Did you set a root password, perhaps?I have not done so to my knowlege, but I have seen several posts reporting the same thing.

It would appear that my 12.04 Recovery menu behaves slightly differently from yours, I just re-tried some of the options again, with the following results:

**Drop To Root Terminal:** >> Message below "Enter Root Password for maintenance, ( or Ctrl+d ) > 'Ctrl+d' returns to the recovery menu.

**Safe mode:** >>Asks confirmation of change to Read/Write and Mounting devices > gives a screen of messages ending with " Fatal Error ", waiting 60 secs returns to recovery menu, entering Ctrl+c gives a black screen and then the normal GUI log-in screen.

**Fsck Check Disks: **>> Asks confirmation of change to Read/Write and apparently does a check taking 20 secs and returns to the menu; System Info option & Menu Title now show "Read/Write mode"

**Activate Internet** connection >>Also asks confirmation and gives a screen full of messages including " Starting Network manager" but fails to connect and reports unable to update cache.

**Dpkg fix broken packages** >> Also asks confirmation and gives a screen full of messages and wants to install nvidia-common 295.40, which would have been a disaster.

So there is away of setting permissions to Read/Write, but no way to make use of it!! +1 to your bug-report.

Chao!, **bogan**.

---

### Post by Paddy Landau on 2012-05-08
> **bogan said:**
> +1 to your bug-report.
To vote, you have to actually [go to the bug report]("https://bugs.launchpad.net/ubuntu/+bug/996454"), click on the green wording, and say that it affects you. Otherwise it may be ignored.

---

### Post by bogan on 2012-05-08
Hi!, **Paddy**,

I did go there, there was not any green wording, but I logged-in and added a comment to your bug-report as there did not seem to be any other option to just vote in support.

I found the Answers> Search function very user-unfriendly and ineffective, had your link not directed me I would never have found it.

Chao!, **bogan**.

---

### Post by Paddy Landau on 2012-05-08
> **bogan said:**
> there was not any green wording...

[LIST]
[*] At the top, under the title, you should see the following:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=217518&stc=1&d=1336479008[/IMG]
[/LIST]
 
[LIST]
[*] Click on the green wording ("Does this bug affect you?") and answer the pop-up question.
[/LIST]

---

### Post by bogan on 2012-05-08
Hi!, **Paddy**,

Right, found it this time, I was looking top right where the log-in option is.

It now says:                                                                                        
                                                   
                                                                        [COLOR=Green][This bug affects you and 1 other person]("https://bugs.launchpad.net/ubuntu/+bug/996454/+affectsmetoo")[/COLOR]           [             [IMG]https://bugs.launchpad.net/@@/edit[/IMG]]("https://bugs.launchpad.net/ubuntu/+bug/996454/+affectsmetoo")but in green.

Chao!, **bogan**.

---

### Post by Paddy Landau on 2012-05-08
> **bogan said:**
> It now says:                                                                                        
                                                   
                                                                        [COLOR=Green][This bug affects you and 1 other person]("https://bugs.launchpad.net/ubuntu/+bug/996454/+affectsmetoo")[/COLOR]           [             [IMG]https://bugs.launchpad.net/@@/edit[/IMG]]("https://bugs.launchpad.net/ubuntu/+bug/996454/+affectsmetoo")but in green.
And now it says 2 other people, so someone else has found it. :)

---

### Post by bogan on 2012-05-08
Hi!, Paddy.

I came across this bit in a Post by Kansasnoob in Re: Pschocats Tutorial Updates:

> Totally off-topic but I should also mention that I was surprised  selecting "root" in recovery mode mounts files and folders as read only  so I first had to enable networking and then select root again to get  read & write capability. That may effect other uses of the recovery  mode :sad:Perhaps you should ask him to vote on your bug-report, if he has not made one himself.

Chao!, bogan.

---

### Post by Paddy Landau on 2012-05-08
> **bogan said:**
> I came across this bit in a Post by Kansasnoob in Re: Pschocats Tutorial Updates:

Perhaps you should ask him to vote on your bug-report, if he has not made one himself.
Bogan, do you have a link for me so I can find the report?

---

### Post by bogan on 2012-05-09
Hi!, **Paddy**,

This is where I found the Kansasnoob quote:[http://ubuntuforums.org/showthread.php?t=416802&highlight=Psychocats+Tutorial+Updates Post #578]("http://ubuntuforums.org/showthread.php?t=416802&highlight=Psychocats+Tutorial+Updates")

I trust that is what you meant.

Chao!, **bogan**.
[ ]("http://ubuntuforums.org/showthread.php?t=416802&highlight=Psychocats+Tutorial+Updates")

---

### Post by Paddy Landau on 2012-05-09
> **bogan said:**
> This is where I found the Kansasnoob quote...
Thank you; I have [post=11919728]posted a reply[/post].

---

### Post by kansasnoob on 2012-05-09
Thanks Paddy, please see:

[http://ubuntuforums.org/showpost.php?p=11920260&postcount=580](http://ubuntuforums.org/showpost.php?p=11920260&postcount=580)

---

