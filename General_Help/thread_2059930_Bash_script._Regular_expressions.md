---
title: "Bash script. Regular expressions"
date: 2012-09-19
forum: General Help
---

### Post by Drenriza on 2012-09-19
Hey guys.

I'am wondering (their probably is) if their is a better / more "beautiful" way or writing a command that does the same as the following command.

```

cat /etc/somefile.txt |sed '/^### Start/d' |sed '/^### End/d'|sed '/^# FI/d' |sed '/^FILM/d'

```

And along with deleting the necessary lines, how would you append 3 lines at the end of the file in one go? Where the lines should be

/video1/*
/video2/*
/video3/*

Is their some cleaver way of adding the /video incrementing a value to get the 1,2 and 3 and then add a /* to the end.

Currently i'am working on getting more into regular expressions (among other things) and was curious to see what you guys would come up with in such a situation.

The lines that i want to delete is all that start with FILM and the following 3 lines
### Start of FILM list - Automatically generated at yyyy-mm-dd xx:xx:xx
# FILM <uniqe film_id> <directory name>
### End of FILM list

Thanks on advance for your time.
Kind regards.

---

### Post by Drenriza on 2012-09-19
What i came up with so far

```

cat /etc/somefile.txt |grep -Ev -e "FILM list" -e "film_id" -e "^FILM"

```

But still wondering if their is a better way :)

EDIT.
I could of course do 
```

cat /etc/somefile.txt |grep -Ev -e "FILM"

```

But would still a way to add the 3 lines in a easy way would be nice.
uhmm.

---

### Post by steeldriver on 2012-09-19
You're probably going to get the 'unnecessary cat' brigade jumping on you ;) For the record there's no need to 'cat' with either grep or sed - both can take the file name as an argument:

```
sed [-e] '**expression**' *yourfile*
``````
grep -Ev '**expression**' *yourfile*
```You *could* do it all in 'sed', using the 'a' command for the append - NB I don't know exactly what regex you need to use for the deletes, you will need to adjust this if there are '#... FILM' lines that yo do NOT want to match

```
$ sed -e '/^#.*FILM/d' -e '$a \
/video1/* \
/video2/* \
/video3/*' *yourfile*
```or you could do the deletes in either sed or grep as you have done already, then append the new lines with something else - even plain old 'echo'

```
echo -e "/video1/*\n/video2/*\n/video3/*" >> *yourfile*
```As always with *nix there are many ways to skin a - *ahem* - cat :)

---

### Post by Drenriza on 2012-09-19
Haha the cat brigade, made me chuckle a bit ,)

Anyways i ended up doing

```

grep -Ev -e "FILM" /etc/somefile.txt |sed '$ a\/video1/*\n/video2/*\n/video3/*\n/trailer/*'

```

I wasn't aware grep and sed could take the file as a argument :p i learned something new.

Can you explain to me if the below is correct. 
```
sed -e '/^#.*FILM/d
```
^ Starts with
# just a symbol
. any character?
* wildcard

But how does this also remove a String if it starts with
FILM someText
instead of
#FILM someText

---

### Post by steeldriver on 2012-09-19
Hi, yes that's pretty much it - except that regex * is a little bit different from the shell glob * (aka wildcard) that you are probably familiar with

^ [COLOR=Red]**line **[/COLOR]Starts with
# just a symbol
. any [COLOR=Red]**single **[/COLOR]character
*** [COLOR=Red]zero or more occurrences of the immediately preceding regular expression[/COLOR]**

so in this case .* means zero or more single characters

> But how does this also remove a String if it starts with
FILM someText
instead of
#FILM someText     
It removes **lines **starting with # and then containing FILM - if you want to remove (or substitute) strings **within **lines you will need the s command instead of the d command

Hope this helps

---

### Post by Drenriza on 2012-09-21
Thanks steeldriver.

Makes perfect sense :)

---

