---
title: "assigning values to bash variables from a file"
date: 2010-06-09
forum: General Help
---

### Post by Cool Javelin on 2010-06-09
Is there an easy way to get a line from a text file into a variable in a bash script?

I have a file called outside_temp that has a single number, say, 63.2

I would like to make a variable in a BASH script have that value.

I know how to use the input redirection and reassignment of stdin using 
exec 6<&0
exec < outside_temp
read current_temp
exec 0<&6 6<&-

but using all those &'s is just too screwy.

Can I use something like
cat outside_temp > current_temp
or
current_temp=$(cat outside_temp)
or something like that?

Thanks, Mark.

---

### Post by Cool Javelin on 2010-06-09
Never mind, the syntax

current_temp=$(cat outside_temp)

worked.

---

