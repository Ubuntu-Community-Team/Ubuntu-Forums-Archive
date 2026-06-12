---
title: "Samba and Secondary Groups"
date: 2012-03-26
forum: General Help
---

### Post by HornedBeast on 2012-03-26
Hello

I am running Samba 3.5.6 and am running into a few problems. Currently, all my Linux users are synced with Samba, as are groups. This appears to work correctly.

I have lots of users whose primary groups are the same, but some who have extra rights as admins or what-have-you. However, Samba seems to be ignoring these "Secondary Groups" completely and only taking into account the Primary Groups.

For example, if I have a share that only allows "admin" group members in, if I set a secondary group of a user to "admin", they still cannot get in (but they can via SSH or system level).

Below is my smb.conf with a few shares removed for simplicity.

I have also posted some example users and groups of how I'd like this to end up:

```

[global]
	lanman auth = Yes
	log file = /var/log/samba/log.%m
	load printers = no
	obey pam restrictions = yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	client plaintext auth = Yes
	dns proxy = no
	netbios name = Server01
	writeable = yes
	server string = My Samba Server
	unix password sync = yes
	workgroup = MyWorkgroup
	client lanman auth = Yes
	os level = 255
	security = user
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000
	directory mode = 775
	create mode = 775
	domain logons = yes
	pam password change = yes
	force group = engineers

[Equipment]
	path = /home/public/Equipment

[Finance]
	valid users = @finance
        force group = finance
	path = /home/public/Finance

[Holding]
	path = /home/public/Holding

[Procedures]
	path = /home/public/Procedures

[Reports]
	path = /home/public/Reports

[Software]
	read list = @engineers
	force group = quality
	path = /home/public/Software

[Standards]
	read list = @engineers
	force group = quality
	path = /home/public/Standards

[Stationary]
	path = /home/public/Stationary

[Tests]
	path = /home/public/Tests

[Projects]
	path = /home/public/projects

[System Files]
	path = /storage/system files
```

As you can see, by default I wish for everything to be saved under the Engineers group, regardless of what group the user belongs to. However, occasionally, a user who has the secondary group of "Quality" or "Finance" should only be able to access those shares. This currently doesn't work as Samba seems to be ignoring the secondary groups entirely.

Users (a nice mixed bag of users with different groups):

```
user1 (Pri: engineers) (Sec: quality, finance)
user2 (Pri: engineers)
user3 (Pri: engineers) (Sec: quality)
user4 (Pri: engineers) (Sec: quality, finance)
user5 (Pri: engineers)
```

The reason I would like all the user primary groups to be engineers is so when a user logs in via SSH, any file or folders they create will still be in the Engineer group. This will also mean I can remove the "force group = engineers" from the Samba config as this will happen at a system level instead.

Groups (Only 3 at the minute):

```
Engineers
Quality
Finance
```

Perhaps someone can shine a light on the problem.

Thank-you in advance!

---

