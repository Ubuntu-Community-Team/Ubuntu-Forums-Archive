---
title: "Defining variables with printf"
date: 2010-03-24
forum: General Help
---

### Post by hombruno on 2010-03-24
Hi friends,

I am trying to use bash 'printf' to format an environment variable.

Doing this I get on the screen just the format I need (underscores mean blank spaces):

prompt> printf "%10s" "1.23"
________1.23

Unfortunately, when this is assigned to a variable, the format disappears:

prompt> X=`printf "%10s" "1.23"`
prompt> echo $X
1.23

Does anyone know what can be done in this case to get a proper format?
Why does not 'printf' respect the left blank spaces when assigning values to a variable?


Thank you for your help,
Juan

---

### Post by rnerwein on 2010-03-24
hi
i think this is what you want:  IFS='\n' X=`printf "%10s" "1.23"`
results in: ______1.23   ( underscores means blank spaces dito. )
note this input field seperator is only valid for this command. if you want to have it all over in your 
script you must set and export it. but if you do that be careful because you changed the default.
for IFS see: man bash

ciao

---

### Post by hombruno on 2010-03-24
Thank you Merwein.
 
 
I had no idea about IFS and your suggestion has completely solved my problems.
 
Regards,
Juan

---

### Post by slakkie on 2010-03-24
No need for IFS:

```

X=$(printf "%10s" "1.23")
echo -e "$X"

```

---

