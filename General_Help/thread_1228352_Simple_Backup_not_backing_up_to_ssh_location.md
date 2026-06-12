---
title: "Simple Backup not backing up to ssh location"
date: 2009-07-31
forum: General Help
---

### Post by arch0njw on 2009-07-31
At one point in time, I had this working.  It has since stopped working.

I am using the following string for my destination (name and pass changed):

ssh://NAME:P***@fronk.local/home/backup/archon

I can ssh to the machine just fine.  However, when I click "Test" in Simple Backup, I get the famous message:  *The selected destination is not writtable with current permissions.  The backups can not be written there.*

Any hints?

I am running this under Kubuntu 9.04.  I have liked this software thus far, but if it isn't going to work... :-(

---

### Post by CrusaderAD on 2009-07-31
I had problems with simple backup too... I swutched to Keep. MUCH BETTER

```
sudo apt-get install keep
```

---

### Post by arch0njw on 2009-08-01
What is Keep's backup format?  I'm having a hard time finding that information.  I don't like the fact that it isn't maintained anymore... have you had to restore from Keep?  How did that go?

What I like about Simple Backup is that it is essentially a front-end for being able to put together a complex tarball.  Even if SB doesn't want to restore, I can open the backups with tar.  It also does incrementals pretty nicely.

---

### Post by Rob_H on 2009-08-01
Maybe the URL format is wrong. Try:

```
fish://username@hostname/path/to/directory
```

---

### Post by arch0njw on 2009-08-01
Stupid smileys...

The password needs to be included in that.  I am going to put spaces in that so the forum doesn't make smilies.

ssh://n a m e : p a s s @fronk.local/path/blah/blah/blah

I had that working at one point.  Now I'm trying to sort out why it doesn't.

---

### Post by Rob_H on 2009-08-01
OK, but did you try replacing "ssh://" with "fish://"?

---

### Post by arch0njw on 2009-08-01
I just tried.  Simple Backup only recognizes ssh or an FTP location.  I am working on reckoning out an FTP alternative, but am really curious why SSH no longer works for this.  It used to, so I'm convinced it can be fixed.

---

### Post by Zill on 2009-08-01
SimpleBackup runs as root so the ssh destination will also need to be writable by root.  I suggest you check/change your permissions on this directory.

---

### Post by NewProggie on 2009-08-02
Hi,

try deleting the .ssh/known_hosts file. I once had this silly error.

```

sudo rm /root/.ssh/known_hosts

```

---

### Post by arch0njw on 2009-08-02
> **NewProggie said:**
> Hi,

try deleting the .ssh/known_hosts file. I once had this silly error.

```

sudo rm /root/.ssh/known_hosts

```

I was hopeful, but that did not work.

Thank you for the suggestion!

---

### Post by arch0njw on 2009-08-10
Now I'm feeling so very stupid.  I got this working.  Here's how.

I switched to a new cable company.  The New Company has their own router they install.  This caused my network to look more like modem-router(theirs)-router(mine) instead of just modem-router(mine).  In getting my resolv.conf reconfigured to use their DNS servers instead of my old ISP's, I also added their router to the list -- a product of sorting out issues at one point.  That was the problem, but it only manifested through SimpleBackup.

After some pondering, I decided to put MY router as a nameserver.  Suddenly, two things happened:
1. My normal ssh into other machines on my network connected faster; it worked with their router as the nameserver, but it took *a long time* to get the password prompt
2. SimpleBackup "just started working again"


So, the "it just stopped working" is a doofus point here.  I changed my network just enough so that, for some reason, CLI ssh and ping could resolve the host name of my target machine, but SimpleBackup could not.

Thanks for all the responses!

---

### Post by arch0njw on 2009-08-10
I'm not finding how to mark a thread as solved, so I'm putting this note here so it will turn up in searches (I hope).

---

### Post by Zill on 2009-08-10
> **arch0njw said:**
> I'm not finding how to mark a thread as solved, so I'm putting this note here so it will turn up in searches (I hope).
Thanks for the update - glad you got it working, :-)

Re the "Solved" tag, this was removed from the forums some time ago.  However, you can still add it manually as you have done with this post.  If you want the start of the thread similarly tagged then you have to edit your first post - there is an "advanced" button somewhere in the edit screen to update the title.  Only the OP can do this so I will leave you to it... :-)

---

### Post by arch0njw on 2009-08-10
> **Zill said:**
> Thanks for the update - glad you got it working, :-)

Re the "Solved" tag, this was removed from the forums some time ago.  However, you can still add it manually as you have done with this post.  If you want the start of the thread similarly tagged then you have to edit your first post - there is an "advanced" button somewhere in the edit screen to update the title.  Only the OP can do this so I will leave you to it... :-)

Cool.  Thanks!

---

