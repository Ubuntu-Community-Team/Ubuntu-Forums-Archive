---
title: "Need help with grep ( i think )"
date: 2012-04-09
forum: General Help
---

### Post by Alphamonkey on 2012-04-09
I am trying to figure out a way to sort a file where there is a bunch of irrelevant info and some relevant information that I need.

the file output from cat looks pretty much like this

irrelevant info irrelevant info irrelevant info
irrelevant info irrelevant info irrelevant info

irrelevant info irrelevant info irrelevant info
irrelevant info irrelevant info irrelevant info

relevant info relevant info relevant info relevant info
relevant info relevant info relevant info relevant info
relevant info relevant info relevant info relevant info

irrelevant info irrelevant info irrelevant info
irrelevant info irrelevant info irrelevant info


So, as far as I can tell I need a way to delimit the newline and only keep sections that have more than two lines between text. Sorry for the ambiguity if more info is needed please let me know I am just not on the computer that has the file right now.

---

### Post by sanderj on 2012-04-09
AFAIK grep is line-by-line program, so it won't do multi-line stuff. Maybe awk and pcregrep can handle it. The pseudo regular expression is something like:

<emptyline><non-empty-line>[3+]<emptyline>

However, I would do it in python. Pseudo-code:

```
text = ""
read next line from file:
 if emptyline:
   if lines-in(text) >=3 then print
   text = ""
 else:
   text = text + thisline
```

---

### Post by Vaphell on 2012-04-09
awk
```
awk 'BEGIN { RS="\n\n"; FS="\n" } NF>2 && $3!=""{ print }' file
```
the trick is to set record separator to double newline and field separator to single line and then check if number of fields in record is greater than 2.
Test for emptiness of 3rd field is needed at the end of file, otherwise last newline would be treated as field separator not as the end of record, so the number of fields would get artificially inflated and 2 line record would return 3. Test for emptiness of 3rd field fixes that.

hm, i think NF>2 is not necessary, $3 not empty should do the trick either way

---

### Post by Alphamonkey on 2012-04-09
Thank you both very much for your response. I am not great at coding and have never used python so I tried awk. The command worked perfectly just as I wanted it to. Thank you so much. You have no idea how much this helps.

Oh, and if you have any good reference info on python I would like to try to start learning it. I have recently started learning shell scripting and really enjoy learning it so I was thinking of either looking into python or perl. I know there is a full thread dedicated to that but if you can recommend one that is clear, concise, and has a lot of relevant examples that would be great because I mainly learn from example and doing.

---

