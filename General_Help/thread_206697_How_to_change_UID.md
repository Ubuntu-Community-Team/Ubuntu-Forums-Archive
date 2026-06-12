---
title: "How to change UID"
date: 2006-06-30
forum: General Help
---

### Post by computerease on 2006-06-30
I have a UID message upon boot and login I must rectify.  It is as follows:

User's $HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owhed and have 644 permissions.  User's $HOME directory must be owned by user and not writable by other users.

Although I have used Linux off & on since circa '96 (Slackware > RH > Mandrake/iva > Xandros [am a Windows trouble/shooter/tech for $$), only recently have I made the move to convert totally to Ubuntu Linux.  I am setting up the network (4 Ubuntu systems; 1 w98, 1dualbootXP).  In working on network drive mounting issues (playing with smb4K, LinNeighborhood and xsmbrowser--Gnome is the GUI), somehow I was able to change my UID from the original 644 to 1000 approx. two days ago.  Upon rebooting today I received the above error message.  I have booted into several renditions of the kernel (breezy and dapper) and the message persists.  In Users & Groups applet I can see the UID as 1000 but cannot change it back to 644.  I simply do not remember how I was able to change it in the first place so I am in a quandry how to change it back and alleviate the error message.  Any assistance would be deeply appreciated.

---

### Post by droazen on 2006-07-03
Well, there is the usermod command...

```

sudo usermod -u uid user_name

```

According to the man page:

```

Any files which the user owns and which are located in
the directory tree rooted at the user’s home directory will have
the file user ID changed automatically. Files outside of the
user’s home directory must be altered manually.

```

I've never tried doing this before, so I'd read the man page carefully before trying it :)

---

### Post by lotheac on 2006-07-03
Umm, 644 permissions does not mean that your UID needs to be 644. By default the first user's UID is 1000. Try this.
```
chmod 0644 ~/.dmrc
```
If you're for some reason not the owner of that file, 'sudo chown $USER:$USER ~/.dmrc'

---

### Post by computerease on 2006-07-07
Thank you for your response.  I discovered approx two days later how confused my question was.  I had, indeed, changed my ID to the root ID and I did change it back only to discover the numbers at which I was looking were for a different purpose than the user ID.  They were permission numbers.  My apologies.  Had I pursued this as I should have, the error would not have been made.  However ....
I still have a problem.  I ran the command you suggested and it did not impact my problem.  It is as follows
I will create a chart to expose the issue.  I will be comparing three computers with Ubuntu and will call them Main, Back and Loft.  Main is the computer with the problem:
                            Permissions
                 Main              Back           Loft
HOME Directory:  1600755           755            755
Filesystem:      1200755           755            755
.dmrc            1600775           600            missing

When I ran the command: sudo chmod 0644 ~/.dmrc
I was asked for the password and then the command supposedly executed and I was returned to the prompt.  However, the Permission number code remained as above:  1600755
Upon reboot the error message [User's $/HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's HOME directory must be owned by user and not writable by other users.] remained in place.

I have the following questions:
1.  Why are the permissions on the Main machine in such total nonconformity to the what I understand to be the permissions grid?
I understand the permissions grid to be as follows:
          Owner      Group     World (Others)
Read      400        40        4
Write     200        20        2
Execute   100        10        1
None      0          0         0
If this is the case, 777 should be the largest permission number that should appear and 000 the lowest.  The computer known here as Main has 1600755. The chmod command did not touch that number.
2.  This system began as a Breezy system and was updated through Synaptic to Dapper.  Could that be the issue for the differences in Permission numbers and does Dapper have additional factors to consider not present with Breezy (or other flavors of Linux releases if my research serves me well)?
3.  Could the fact that I've modified my system to allow for a Root login have had an impact on the presentation of the Permission numbers?
4.  I HAD changed my user number from 1000 to the root number at one time but changed it back.  Could that have diddled the system?
5.  Am I seeing the symptoms of something other than simple user numbers and Permissions numbers here, such as a security breach of some type?
6.  Should this question be in a different location on the forum for ease of access and reply?
Thank you in advance for your time and consideration.
By the way:  This is what I call fun.  On Windows I work as an intransigent problem trouble shooter and thrill to the chase of defeating problems or understanding why they are permanent.  As the definition of Windows is: Intransigent problems waiting to manifest, I have a lot of fun there.  But windows is guaranteed to remain a dog because they've decided to market malware removal software rather than correct their problems.  Mr. Fox, would you please come and guard my hen house?

---

### Post by lotheac on 2006-07-07
As for your first question, that does seem bizarre. Where did you get those numbers? You're correct in that octal notation for permissions should only have three (four) digits. So I'm afraid I can't help you with that...

Number two: No. Unless I'm horribly mistaken file system permissions function in the same way on all Unix-like systems.

Another question I could speculate on is number four. I don't have experience with changing uid's either, but it doesn't strike me as safe to change your uid to 'the root number' if that's what you've done.

Just for reference, I checked my .dmrc and its permissions are not 0644, but 0600. Also it doesn't hold much information.
```
[Desktop]
Session=gnome
```

I really have to admit I don't know what you should do. I could suggest you to look for other files in your home directory that might not be owned by you or have the correct permissions, but you said even your filesystem root has weird permissions. I'm baffled.

I hate advicing people to reinstall, so I won't do that. But, if that's where you end up, I'd suggest that you just grab your important documents, configs and other files and empty any and all partitions.

---

