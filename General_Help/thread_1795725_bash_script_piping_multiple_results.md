---
title: "bash script piping multiple results?"
date: 2011-07-03
forum: General Help
---

### Post by jingo_man on 2011-07-03
hi guys

i am writing a bash script that i hope can be used with "get_iplayer" to automate the specific shows i would like to download from the iPlayer platform.

i used to use some GUI's for this, but they have ended up breaking and/or didnt offer appropriate support.

so i downloaded the core get_iplayer application/scripts.

i manually download the shows i am interested in with a search string like:

```
get_iplayer-2.79/get_iplayer Zane\ Lowe | grep Zane\ Lowe | awk '{print $1}'
```this returns something like
> 13140:
13141:
13142:
13143:i need to strip of the trailing ":" from each line, then pass these values as a variable to the following string:

```
get_iplayer 13151 --modes radio --modes iphone,flashaac --get --output  ~/Downloads/iPlayer\ Downloads/Zane\ Lowe/
```so questions:
1. can i pipe the 2nd code exert above to the end of the 1st code exert? so for each of the 4 results, it will execute the last command?

2. failing the above, can i put the 1st code exert as the "for i in 'code'", which will automatically go through the loop of 4 results?

3. i guess the last option is to use variables or temp files to output the results of the 1st code exert. and then use that as the source of the loop structure for the 2nd code exert?

hoping i haven't overcomplicated what i think should be a simple issue...

many thanks!

---

### Post by nothingspecial on 2011-07-03
There are probably better ways of doing this with get_iplayer itself, however to use what you've posted

```
for i in $(get_iplayer --type=radio Zane\ Lowe | grep Zane\ Lowe | awk '{print $1}'); do
get_iplayer --g "${i%:}" --modes radio --modes iphone,flashaac;
done
```

for i in $(blah blah blah) puts the output of the commands in the ()s into the variable $i

"${i%:}" in the second line is the result of the first line with the trailing : removed

[COLOR="Red"]for [/COLOR]blah blag blah; [COLOR="Red"]do[/COLOR]
blah blah
[COLOR="Red"]done[/COLOR]

Takes each result of blah blag blah and passes it to blah blah one at a time.

---

### Post by jingo_man on 2011-07-03
thanks, @nothingspecial

that worked a treat!

and yes, i do think that get_iplayer has some PVR type functionality. and i may take a further look into it now that i have an easier, automated means of downloading the files each week.

and thanks for explaining the mechanism - more than helpful for any future uses...

---

### Post by nothingspecial on 2011-07-03
No problem :)

Enjoy Zane Lowe,

I prefer Mike Davies' punk show :guitar:

---

