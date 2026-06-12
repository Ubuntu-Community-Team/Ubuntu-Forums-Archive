---
title: "Help: Script driving me nuts with if statements?"
date: 2010-10-21
forum: General Help
---

### Post by leesiulung on 2010-10-21
I for the life of me is having a hard time with some scripting in Dash with branching statements. What the heck?

I read many tutorials all over the net and none of the codes work. They suggest all sorts of variations, but it ain't working for me. 

Can anyone tell me why the code below always return "Y"?


```

#!/bin/sh
clear

echo -n "---> Enter Y or N? "
read answer
if [ "$answer"="Y" ] ; then
echo "Y"
else
echo "N"
fi

```

Perhaps someone can give me a short explanation on how if statements work?

So far my linux experience has been nothing, but a frustrating mess.

---

### Post by James78 on 2010-10-21
```
#!/bin/sh
clear

echo -n "---> Enter Y or N? "
read answer
if [ "$answer" = "Y" ]; then
  echo "Y"
else
  echo "N"
fi 

```
Edit: What'd I do? I added a space between the operator.

---

### Post by oregonbob on 2010-10-21
James has it. If you don't insert spaces before/after the "=" it assumes you are assigning a value (making answer=Y). It assigns the value fine and therefore it is always true.

---

### Post by DaithiF on 2010-10-22
> **oregonbob said:**
> James has it. If you don't insert spaces before/after the "=" it assumes you are assigning a value (making answer=Y). It assigns the value fine and therefore it is always true.

to be slightly picky (though without changing the overall conclusion, which is absolutely correct), assignment doesn't happen in this case.  in fact "$answer"="Y" just gets treated by the test operator as a (single) string, which is equivalent to the test **[ -n string ]** which basically tests for a non-zero length string.  

and that concludes my daily quota of petty pedantry :)

---

### Post by leesiulung on 2010-10-22
Thanks guys!

---

