---
title: "Bash script, removing windows return characters."
date: 2010-09-01
forum: General Help
---

### Post by Grenage on 2010-09-01
Hi there,

I've got a basic script, which parses data from a text file and performs actions based on that data.  Here is my code:

```
dsrc="/home/russellm/sites/"
ddst="/home/russellm/othersites/"

while read SiteID
do
        if [[ ! -d "$ddst${SiteID:0:1}" ]]
        then
                mkdir "$ddst${SiteID:0:1}"
        fi
        mv "$dsrc${SiteID:0:1}/${SiteID%*}" "$ddst${SiteID:0:1}/" | tr -d '\r'

done < sites.txt
```

Problem being, the text file came from a windows system, and contains those return characters (\r).  I 'could' just run the whole thing through *tr* and then run the script on the new data file, but I'm looking for a more elegant solution.  As the code above shows, I'm trying to pipe the mv command though tr in order to remove the return character - but it's not working.  I can't get this to work with sed either, so I know I'm doing something wrong.

I also tried to remove it using ${SiteID%\r} - but that also failed.  The characters don't show up in an echo, just when executing a command.

Output example (emphasis mine):

```
mv: cannot stat `/home/russellm/sites/B/B23467324**\r**': No such file or directory
```

I'm tempted to just convert the file once and call it a day, but you know what it's like.

EDIT: To be honest, I'm starting to suspect that there are no return characters, and that I'm going about this wrong.

---

### Post by Vaphell on 2010-09-01
maybe i'm missing something here but can't you just do it the lame way in 3 steps? 1. store the string in some variable 2. pass the variable through tr 3. use the variable in mv? i think your tr is too late, it works on the mv output not parameters?

---

### Post by Grenage on 2010-09-01
> **Vaphell said:**
> maybe i'm missing something here but can't you just do it the lame way in 3 steps? 1. store the string in some variable 2. pass the variable through tr 3. use the variable in mv? i think your tr is too late, it works on the mv output not parameters?

No, I doubt you're missing anything; I'm a noob when it comes to code.  I figured that the mv command would get piped through tr, which would strip the characters, then output the remainder.  I thought that was probably the best way to go about it.

---

### Post by spjackson on 2010-09-01
Move the 'tr' as follows.

```
dsrc="/home/russellm/sites/"
ddst="/home/russellm/othersites/"

tr -d '\r' < sites.txt | while read SiteID
do
        if [[ ! -d "$ddst${SiteID:0:1}" ]]
        then
                mkdir "$ddst${SiteID:0:1}"
        fi
        mv "$dsrc${SiteID:0:1}/${SiteID%*}" "$ddst${SiteID:0:1}/"

done
```

---

### Post by Grenage on 2010-09-01
> **spjackson said:**
> Move the 'tr' as follows.

I had no idea that it could be injected into the while loop that way.  It works a treat, thank you very much!

---

