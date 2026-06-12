---
title: "SED: how to use replace using the output of another command."
date: 2011-05-06
forum: General Help
---

### Post by quickk on 2011-05-06
Hi everyone, 

   I have a list of contest participant names in a file.   I also have a certificate of participation for the contest, that is addressed to a generic "Jane Doe".   I want to read the list of names in the file, and then use sed to replace "Jane Doe" with these names and export a new certificate for each name. 

Basically, I would like to do something like this:

```

j=0
while read line
   do echo -e "$line" | (somehow write the output of the echo command to a tmp variable)
   sed -e 's/'Jane Doe'/'$tmp'/g' oldcertificate > newcertificate$j
   j=$(($j+1))
done < listofnames_file

```

I just don't know how to take the output of a command and replace "Jane Doe" with this output.  

Any help would be greatly appreciate.  I've looked around for a couple of hours and can't find what I need :(.

---

### Post by amauk on 2011-05-06
The name of the participant is in the variable $line

You're iterating through listofnames_file, and with each iteration the next line of the file is stored in $line

So you can simply do
```
#!/bin/bash
j=0
while read line; do
	sed -e "s/Jane Doe/$line/g" oldcertificate > newcertificate$j
	j=$(($j+1))
done < listofnames_file
```

*edit*
Oops,
You also need double quotes around the sed expression, else the bash variable won't be evaluated

---

### Post by quickk on 2011-05-06
Doh!  Thanks for the quick reply!  I'm still very new to this bash scripting, so I don't quite know the basics yet.   

If I may, I have one more complication.   Unfortunately, the listofnames_file has a bunch of other fields after the names on each line.  Each field is comma delimited, so I figured out how to get the names only like this: 

```
while read line; do
  echo -e "$line" | cut -d "," -f1 
done < listofnames_file

```

Now I need to get the output of the cut command into a variable, and then into sed.

---

### Post by quickk on 2011-05-06
I figured it out!

```
while read line; do
  tmp=$(echo -e "$line" | cut -d "," -f1) 
done < listofnames_file
```

Thank you for your help amauk, I really appreciate it! :)

---

