---
title: "grep - trying to find users within group X"
date: 2011-09-05
forum: General Help
---

### Post by afd on 2011-09-05
Hi,

I've not used grep before and so am struggling right at the beginning of what is likely to become a steep learning curve.

I am trying to output users from /etc/passwd where they are in groupX or groupY within /etc/group.

I got this far:

```
egrep 'groupX|groupY' /etc/group
```

And this seems to output the groups found in /etc/group.

Next stage is to match users in /etc/passwd where the users are in groupX|groupY etc.

Any hints or tips on how to do this?

Thanks.

---

### Post by Charlietje on 2011-09-05
use the following:

```
groups groupX
```

and it shows all users in that group

---

### Post by Toz on 2011-09-05
```
for line in `egrep 'groupX|groupY' /etc/group | cut -d':' -f4`; do grep $line /etc/passwd; done
```

EDIT: sorry, won't work if there are more than 1 members in the group.

EDIT: Try this one instead:

```
for line in `egrep 'groupX|groupY' /etc/group | cut -d':' -f4-`; do grep $line /etc/passwd; done
```

---

### Post by sisco311 on 2011-09-05
Well, you can probably do it in awk, but here is how to do it in bash:
```

#!/bin/bash

group1="video"
group2="audio"

while IFS=: read -r group _ gid users
do
    if [[ "$group" == "$group1" ]] || [[ "$group" == "$group2" ]]
    then
        # save the usernames in an array
        { IFS=, userlist+=($users); }
        # save the gid in another array
        gidlist+=("$gid")
    fi
done < /etc/group

# print the uniq usernames:
printf '%s\n' "${userlist[@]}" | sort -u
# print the gids:
printf '%s\n' "${gidlist[@]}"

```

A user is not necessarily listed as a member of its primary group in /etc/groups. That's why you have to store the gids. You will have to check in /etc/passwd that the gids are or aren't the a primary gid of a user.

---

