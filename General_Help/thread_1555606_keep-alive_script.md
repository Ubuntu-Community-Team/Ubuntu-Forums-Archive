---
title: "keep-alive script"
date: 2010-08-18
forum: General Help
---

### Post by manfromthezoo on 2010-08-18
Good afternoon, pop-pickers.

Having trouble with a script I'm writing, that I intend to execute every 15 minutes as a cron job. It's supposed to ping the server specified to check it's responding.

If it is, it dumps an 'all is well' message down /dev/null (left in place like that because I might change it later), bombs out, and that's it job done.

The idea is that is a response isn't received, it emails me. Trouble is, the ping section just repeats itself ad infinitum, emailing me again, and again, and again....

What I want it to do is do one set of ping checking, and email me ONCE if there is no response. Anyone got any ideas? Thanks in advance.

Code:

```
i=2
while [ $i -eq 2 ];do

ping -c 5 10.0.0.204
 if [[ $? == 0 ]]

then
echo "Server up" > /dev/null
i=0
else
mail -s "Server down" email@addy.com < messagecontent.txt
fi
done
```

---

### Post by cdenley on 2010-08-18
> **manfromthezoo said:**
> What I want it to do is do one set of ping checking, and email me ONCE if there is no response.

Then why did you use a while loop?

---

### Post by DaithiF on 2010-08-18
if you're running it regularly under cron, why the while loop in the script?  just have the script run once regardless of whether the pings succeed or not, e.g.:

```
ping -c 5 10.0.0.204
if [[ $? == 0 ]]; then
        echo "Server up" > /dev/null
else
        mail -s "Server down" email@addy.com < messagecontent.txt
fi

```

---

### Post by manfromthezoo on 2010-08-18
Why did I use a while loop?

Good question. Lack of caffeine / available blood sugars / lunacy. Just delete as appropriate. :lolflag:

Thank you both for your help.

---

