---
title: "Sending output to /dev/null oddity"
date: 2009-08-13
forum: General Help
---

### Post by cmfarley19 on 2009-08-13
I have written a script (originally seen in Linux Journal) for a twitter command line client.
the key line(s) of the script are as follows:
```
$curl --basic --user "$user:$pass" --data-ascii \
  "status=`echo $@ | tr ' ' '+'`" \
  "http://twitter.com/statuses/update.json"
```
This works wonderfully except that is spits out copious output.  So I added a simple "> /dev/null" to the end.  I would expect to see nothing after hitting enter, save for the next command line prompt, but I am now getting different output that looks like this:
```
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1096  100  1085    0    11   1395     14 --:--:-- --:--:-- --:--:--  1644
```
Does anyone have any idea a) What this is? b) where it comes from, or c) how to get rid of it.

Thanks,

Chris

---

### Post by DaithiF on 2009-08-13
Hi,
its a progress meter displayed by curl.

you can suppress it a couple of ways:
add the -s flag to the curl command (-s = silent)
or
redirect stderr to stdout (which you have already redirected to /dev/null).  so the end of your command would look like:
> /dev/null 2>&1

---

