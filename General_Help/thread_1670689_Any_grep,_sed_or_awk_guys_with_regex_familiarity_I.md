---
title: "Any grep, sed or awk guys with regex familiarity? I need some help."
date: 2011-01-19
forum: General Help
---

### Post by draperdt on 2011-01-19
Hi guys,

I have an xml file. The file looks like this, [PHP]<manufacturer_data>
<action>INSERT</action>
<mfr_id>100700</mfr_id>
<local_content>0</local_content>
<name>Tyson Foods, Inc./Dinner Meats</name>
</manufacturer_data>
[/PHP]

Its a huge file [1GB], so I cannot even open it using text editors etc. I need to extract mfr_ids from the file to do some analysis and comparisions.

I am pretty noob with text parsing and extraction. I want to know which tool and how to extract this info. 

Right now if I use [PHP]cat infile | grep mfr_id[/PHP] prints the complete rows like so, [PHP]<mfr_id>10</mfr_id>
<mfr_id>100280</mfr_id>
<mfr_id>100378</mfr_id>
<mfr_id>100403</mfr_id>
<mfr_id>100699</mfr_id>
<mfr_id>100700</mfr_id>
<mfr_id>100761</mfr_id>
<mfr_id>100902</mfr_id>
<mfr_id>101383</mfr_id>
<mfr_id>101414</mfr_id>
<mfr_id>1016</mfr_id>
[/PHP] I want just the numbers. How would I do that?

Also, I want to know how to extract something similar based on a condition. Such as <name> based on <mfr_id>
such as [PHP] cat infile | grep **<name>** WHERE <mfr_id>=xyz  [/PHP] some like that....I know thats an abomination to grep syntax but I dint know how else to explain, Sorry.


Any help would be greatly appreciated, Thanks guys.

---

### Post by dracayr on 2011-01-19
to ectract the mfr_ids:
```

cat infile | grep mfr_id |sed -e "s/<mfr_id>\(.*\)<\/mfr_id>/\1/"

```
to get the name depending on the mfr_id:
```

cat test|grep "<mfr_id>100701</mfr_id>" -A 2|grep name|sed -e "s/<name>\(.*\)<\/name>/\1/"

```
You'll have to change that one a bit if you want anything other than the name -- obviously you'll have to change the sed command, but also the first grep command. The -A 2 option means that it will include the two lines after the match in the output (since <name> is two lines below mfr_id). If you want the <action>, for example, use -B 1 instead of -A 2.

---

### Post by benson444 on 2011-01-19
You can strip out the tags with this sed command:

```
grep 'mfr_id' filename | sed 's/<[^>]*>//g'
```

I think that's right. It worked for a quick test file I made.

---

