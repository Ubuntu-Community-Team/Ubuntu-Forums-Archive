---
title: "Simultaneously run multiple commands from bash script"
date: 2010-09-21
forum: General Help
---

### Post by sbarrow on 2010-09-21
I'm trying to write a bash script that will simultaneously ping a host and execute a traceroute at the same time. I would like the results to output to a text file. 

Any help would be appreciated. 

Thanks

---

### Post by Tibuda on 2010-09-21
you can use "&"
```
#!/bin/bash
rm output.log
command1 >> output.log &
command2 >> output.log &

```

---

### Post by Bachstelze on 2010-09-21
> **Tibuda said:**
> you can use "&"
```
#!/bin/bash
rm output.log
command1 >> output.log &
command2 >> output.log &

```

That's not a very good idea because the output from both commands will be mixed in the file. Better make both command output to a separate file and concatenate those after they have finished.

Though of course when the commands run in the background, it's not easy to know when they finish...

---

### Post by Tibuda on 2010-09-21
> **Bachstelze said:**
> That's not a very good idea because the output from both commands will be mixed in the file. Better make both command output to a separate file and concatenate those after they have finished.

Though of course when the commands run in the background, it's not easy to know when they finish...

it is not hard. you can use "wait".

```
#!/bin/bash
command1 > /tmp/output1.log &
command2 > /tmp/output2.log &
wait
cat /tmp/output{1,2}.log > output.log
rm /tmp/output{1,2}.log

```

EDIT: See [http://unstableme.blogspot.com/2008/06/bash-wait-command.html](http://unstableme.blogspot.com/2008/06/bash-wait-command.html)

---

### Post by Bachstelze on 2010-09-21
Indeed, I don't know how I forgot about wait. ^^;

---

### Post by sbarrow on 2010-09-21
ok here is my bash script. 

ping [www.website.com](www.website.com) -c 30 >> output.log &
wait
sudo traceroute [www.website.com](www.website.com) >> output.log &

The output is not being mixed together, and weren't even before the wait command but threw it in anyway. My question is now, does the wait command prevent both commands from running at the exact same time?

---

### Post by Tibuda on 2010-09-21
> **sbarrow said:**
> ok here is my bash script. 

ping [www.website.com](www.website.com) -c 30 >> output.log &
wait
sudo traceroute [www.website.com](www.website.com) >> output.log &

The output is not being mixed together, and weren't even before the wait command but threw it in anyway. My question is now, does the wait command prevent both commands from running at the exact same time?

They are not running simultaneously in your script. The script is waiting for ping to finnish before it starts traceroute. This is how it is supposed to be:
```
#!/bin/bash
ping $1 -c 30 >> /tmp/ping.log &
sudo traceroute $1 >> /tmp/traceroute.log &
wait
cat /tmp/{ping,traceroute}.log > $2
rm /tmp/{ping,traceroute}.log
```

---

