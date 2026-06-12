---
title: "Detailed infos about all users in a file?"
date: 2009-12-29
forum: General Help
---

### Post by shade5 on 2009-12-29
Hi,

I need to know the infos about users like which groups they are in or name etc. It should be in a text file. Does this exist or do I have to script?

Thanks.

Edit: Solved it. /etc/groups solves my problems.

Edit2: /etc/groups did not solve all problems.

---

### Post by iMisspell on 2009-12-29
The following will save a list of users (theres two options) and the groups they belong to, to a file.

I do not know how to save "command results" to a variable in bash, so i first save the list of user names to a file, read that file for the names, clear the file, and then save the user-group back to the file. 
So in short, this is a *very very crud* way of going about this, but will get the job done in-till a more skilled scripter posts something for you.

Will save results to 'UsersAndGroups.log'
```

#!/bin/bash

# 0 will list off /home/UserName's
# 1 will list off all user accounts (www-data, mysql, daemon, syslog, etc.)
allUsers=1;


if [[ -e "UsersAndGroups.log" ]] ; then
	cat /dev/null > 'UsersAndGroups.log';
fi


if [[ "$allUsers" == 1 ]] ; then
	gawk -F: '{ print $1 }' /etc/passwd > 'UsersAndGroups.log';
else
	ls /home > 'UsersAndGroups.log';
fi

num=0
for user in `cat UsersAndGroups.log`; do
	users[$num]=$user;
	num=$(($num + 1))
done
cat /dev/null > 'UsersAndGroups.log';

users_count=${#users[@]};
for (( i=0;i<$users_count;i++)); do
	groups ${users[${i}]} >> 'UsersAndGroups.log';
	#groups ${users[${i}]};
done

```

[edit]
> Last edited by shade5; 9 Minutes Ago at 02:10 AM.. 
ok, so it took me around 10 mins to come up with this :)
Maybe it will be a stepping stone for someone else.

Glad you figured it out.
_

---

### Post by shade5 on 2009-12-29
Nevermind. Because now I got a problem again so your script might rescue me. I will try it and tell if it worked.

---

