---
title: "editing my .bashrc to simplify a command"
date: 2010-09-03
forum: General Help
---

### Post by jon.reeve on 2010-09-03
Hi, I want to write a little bit of code to make it easier to look up a word with wordnet (the "wn" command) and add it to my vocab list. 

In other words, instead of typing ```
wn filibuster -over && wn filibuster -over >> vocab.txt
``` to look up definitions for the word "filibuster" and add it to vocab.txt, I want to be able to type ```
d filibuster
``` and have it know what to do. 

I tried adding this to my .bashrc: 

```
d() {
	wn "$" -over && wn "$" -over >> vocab.txt
	}
```

but it doesn't seem to be working. I've almost never written any scripts before, so I don't know what I'm doing wrong (or not doing). Any help would be much appreciated.

EDIT: Never mind, figured it out. Apparently I have to use "${1}" instead of "$".

---

### Post by lykwydchykyn on 2010-09-03
First, why are you running the command twice?  If the goal is to both put the output to a file and see it on the console, I'd suggest using tee (see below).

Second, you want to replace "$" with "$1".

So the code should be:
```

d()
{
wn "$1" -over |tee -a vocab.txt
}

```

EDIT: Ah, I see you figured it out.

See if that works.

---

### Post by AlphaLexman on 2010-09-03
Here is another popular version ->
```
    function define ()

    {

        lynx -dump "http://www.google.com/search?hl=en&q=define%3A+${1}&btnG=Google+Search" | grep -m 8 -w "*"  | sed 's/;/ -/g' | cut -d- -f1 > /tmp/templookup.txt

        if [[ -s  /tmp/templookup.txt ]] ;then   

            until ! read response

            do

                echo "${response}"

            done < /tmp/templookup.txt

        else

            echo "Sorry $USER, I can't find the term \"${1} \""            

        fi
   
        \rm -f /tmp/templookup.txt

    }


```

---

### Post by inameiname on 2010-09-03
I use the same as AlphaLexman's suggestion and never have issues. Very simple and easy to use.

---

### Post by jon.reeve on 2010-09-03
Thanks for all the great help. This "tee" command looks like it's going to be useful.

---

### Post by JohnElway on 2010-09-03
This isn't necessary at all, but I always put my aliases in a different file (~/.bash_aliases) to keep the default ~/.bashrc info separate from my custom aliased commands. There is a recommendation to do this in the ~/.bashrc file itself but I'm sure this is for organizational preference only.

---

