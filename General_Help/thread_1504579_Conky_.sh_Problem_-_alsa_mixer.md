---
title: "Conky .sh Problem - alsa mixer"
date: 2010-06-08
forum: General Help
---

### Post by luceerose on 2010-06-08
I'm having a frustrating problem with a .sh script.
It's a fairly simple script to get a volume readout in Conky.

I refer to the .sh file in my Conky file as such;
```
${execi 1 /home/larsenguitars/Scripts/Conky/conky_volume.sh}
```
The .sh script itself looks like;
```
#!/bin/bash
mute=`amixer get [COLOR="Red"]Front[/COLOR] | grep "Front Left:" | awk '{print $7}'`
if [ $mute == "[on]" ]
then
    vol=`amixer get [COLOR="Red"]Front[/COLOR] | grep "Front Left:" | awk '{print $5}' | grep -oE "[[:digit:]]{1,}"`
    if [ $vol == "0" ]
    then
        echo "Mute"
    else
        echo $vol%
    fi
else
    echo "Mute"
fi
```

Now, I've highlighted the part I want changed.. I'm trying to get the Master volume here, but the script only seems to work with 'Front' or 'Surround'.
If I try to substitute that parameter with any other amixer control, (Master, PCM, Center, Headphone, etc...),
then I get this error in terminal;
```
/home/larsenguitars/Scripts/Conky/conky_volume.sh: line 3: [: ==: unary operator expected
```

It seems to be talking about; [COLOR="Magenta"]if [ $mute == "[on]" ][/COLOR]
What else would it be expecting and why does it work using Front & Surround but nothing else ?
I've attached a pic. The volume script I'm trying to get working is just under the clock.
I'd really love to get the Master volume working on this. Any Ideas ?

---

### Post by geirha on 2010-06-08
Firstly, if mute is empty, the command will expand to [  == "[on]" ], which gives an error since lhs of = is missing.

```
$ [  == "[on]" ]
bash: [: ==: unary operator expected

```

For this reason, it's a good idea to always quote expansions. "$foo" instead of $foo, "`foo`" instead of `foo`.

Secondly though, you shouldn't use the [ command in bash-scripts. Use the more powerful [[ keyword. See [http://mywiki.wooledge.org/BashFAQ/031](http://mywiki.wooledge.org/BashFAQ/031)

---

### Post by luceerose on 2010-06-08
[SOLVED]
I found a solution.
There's a few people I've found having similar volume problems with Conky that will love this. From what I can tell, the style of script I was using is basically useless in the newer versions of Conky. It works on some channels but not others. Anyway, Ive found a script that works. I haven't tested it on everything yet, but it works on Master which was what I was wanting in the first place.
Obviously, this is an .sh script & must be referred to in the usual way by using an exec, execi, texec or texeci command. Anyway, here it is;
```
#!/bin/bash
amixer get Master | awk -F'[]%[]' '/%/ {if ($7 == "off") { print "Master Mute" } else { print "Master",$2"%" }}'
```

---

### Post by cheway on 2012-06-06
Sorry for resurrecting an old thread, but just a quick note to say thank you. I really didn't want to resort to a script to do this (conky from the 12.04 repositories doesn't support alsa it would seem with some serious jiggery pokery), but this was the simplest one I found.

I just made a few changes. Firstly, I wanted a bar rather than a percentage, which I did with the line (this is in the conky config file)...

```
${execbar /home/matthew/.conky/volume.sh}
```

...but for that to work, the output has to be numerical only, so I changed the script to look like this...

```
#!/bin/bash
amixer get Master | awk -F'[]%[]' '/%/ {if ($7 == "off") { print "mute" } else { print $2"%" }}'

```

You'll also notice I changed it from "Mute" to "mute" - that capital 'M' was just completely unacceptable :)

Thanks again for the solution, this one had me stumped.

Cheers,
Matt.

---

### Post by oldos2er on 2012-06-06
Please don't bump old threads.

---

