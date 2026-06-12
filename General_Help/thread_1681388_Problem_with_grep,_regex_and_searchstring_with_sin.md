---
title: "Problem with grep, regex and searchstring with singlequotes"
date: 2011-02-04
forum: General Help
---

### Post by bovisfeldt on 2011-02-04
At my work i have a legacy web system that tells the id of documents based on some given variables. this information can be used in another system to retrieve the needed file.

I am trying to automate this, and have managed to feed the variables and download the correct page using wget. The result is a result.php page with a lot of embedded info.

The information i am looking for is enclosed in single quotes on a line like this:[B]
requestedForm: '1234',[/B]

the information i want is the **1234** part.

i thought i could do like this from bash:
$idnumber = grep "requestedForm: '(.*?)'" result.php

but I always get an empty string back... any idea what i am doing wrong?

---

### Post by DaithiF on 2011-02-04
Hi,

```
> id=$(grep requestedForm somefile | sed "s/^.*'\([0-9]\+\)'.*/\1/")
> echo $id
1234

```

grep picks out the line of interest, it gets piped to sed which gets rid of the leading and trailing stuff.

you need the $( ... ) construct to execute a command and capture its result, and when assigning this to a variable ('id' in this case), its important that there are no spaces between the variable name and the start of the $( ...etc

---

