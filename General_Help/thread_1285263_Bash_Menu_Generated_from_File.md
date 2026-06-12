---
title: "Bash Menu Generated from File"
date: 2009-10-07
forum: General Help
---

### Post by mastermindg on 2009-10-07
I'd like to generate a menu in bash from a text file. I've got a list of items that I'd like to supply as options in my script. This is what I've got so far:

```
echo "Select your channel:"
select channel in $(cat /home/user/channellist)
do
	echo "You picked $channel ($REPLY), processing..."
done
```

---

### Post by mastermindg on 2009-10-07
I've managed to use curl to fetch the page. Now I just need to parse it into the listings that I need. Any suggestions?

---

### Post by mastermindg on 2009-10-08
I ended up using a python sript - HTML2CSV.py - google it. From there I used sed to break it down to it's elements and format it.

---

