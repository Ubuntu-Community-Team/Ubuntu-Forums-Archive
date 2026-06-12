---
title: "Home Fileserver"
date: 2010-01-16
forum: General Help
---

### Post by Duncan J Murray on 2010-01-16
Hello, can anyone provide any suggestions for creating a home fileserver.  I am thinking of putting one together, but know very little about servers.  The purpose of it is to:

1. Provide large storage space for music, videos etc for laptops around the house
2. Automatically back-up these files in case of a harddrive failure.
3. Allow the same files to be accessed easily from different computers
4. I don't actually need it to provide my files over the internet

For it to work, I really need the system to be sort-of transparent.  I'd like the folder to appear on my laptop computer without any fuss, requirement for passwords or needing mounting etc...  Just as if I'd plugged in my external harddrive.

Thanks in advance for suggestions on how to do this.

I've drawn a diagram which I think describes what I was thinking of doing...

---

### Post by guitar_man on 2010-01-16
You can do install OpenSSH on the file server.
You can acess the files via nautilus from your Ubuntu laptop..

Set your server hard-drives on RAID.
Hope you get the idea..

---

### Post by Iowan on 2010-01-16
[FreeNAS]("http://freenas.org/freenas") is one option.

---

### Post by Duncan J Murray on 2010-01-17
I'll look into that, thanks.

Is it easy to configure a RAID array in an old desktop computer, or do you need specific hardware?

Thanks,

Duncan.

---

### Post by Duncan J Murray on 2010-01-17
Oh - just read on the freeNAS website that is supports software RAID!

---

### Post by 3rdalbum on 2010-01-17
I have a home server. It does torrents and file serving.

It's rather easy to set up:

1. Install Ubuntu on the server (desktop edition is fine)
2. Install the "system-config-samba" package, which pulls in the Samba server.
3. Use the "Users and Groups" program to set up a user account that all your clients will use (this is optional - you can enable guest access in Samba if you'd prefer not to have to log in)
4. Go to System > Administration > Samba. If you want authentication from your user account, then set it up in this program as a Samba user. Then click the + (add) icon to create a new share. Give it a name with no spaces, and tick the boxes for what users you want to be able to access it (or optionally, just use "Allow all users").
5. When you've created the share, Samba will be restarted. The next time your clients log in, they will be able to access the share via Places > Network. You can also add a bookmark for your share once you've mounted it.

---

### Post by Duncan J Murray on 2010-01-17
Thanks, that sounds relatively simple!

I see that I'm going to have to do some experimenting.

I'm currently trying to get hold of a cheap, old computer to do the business.  Just spotted am old server on ebay, but I think it will go for more than I'm willing to spend.  I'm trying to think of some way to make the system automatically backed-up.

Thinking something along the lines of having two harddrives and using rsync to have one drive as the back-up.  Or I could use software RAID, but then I'd have to back that up, too - maybe to a tape-drive?!

Duncan.

---

