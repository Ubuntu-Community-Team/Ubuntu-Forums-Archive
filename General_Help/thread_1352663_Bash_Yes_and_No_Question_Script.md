---
title: "Bash: Yes and No Question Script"
date: 2009-12-11
forum: General Help
---

### Post by User3k on 2009-12-11
I just started getting into writing bash scripts. The very, very, very basics. I am doing well so far, it's fun.

What I want to do is create a script that has yes and no options. If someone types Yes it gives one reply, and no gives a different one. Can anyone reply with a basic #!/bin/bash script to show me what I need to do? No explanations are needed, I will figure it out.

Also a side question. If I wanted to execute another bash script could I do that? For example lets say I have 1.sh, 2.sh and I wanted 1.sh to execute 2.sh and when 1.sh does this it closes, could I do that? I hope I explained that right. Did I mention I was very, very, very new to this ;) lol

---

### Post by kaibob on 2009-12-11
> **User3k said:**
> What I want to do is create a script that has yes and no options. If someone types Yes it gives one reply, and no gives a different one. Can anyone reply with a basic #!/bin/bash script to show me what I need to do? No explanations are needed, I will figure it out.

Try this.

```
#!/bin/bash

read -p "Enter yes or no: " RESPONSE

if [ "$RESPONSE" = yes ] ; then
   echo "You answered yes!"
elif [ "$RESPONSE" = no ] ; then
   echo "You answered no!"
else
   echo "You did not make a valid selection!"
fi
```

---

### Post by User3k on 2009-12-11
> **kaibob said:**
> Try this.

```
#!/bin/bash

read -p "Enter yes or no: " RESPONSE

if [ "$RESPONSE" = yes ] ; then
   echo "You answered yes!"
elif [ "$RESPONSE" = no ] ; then
   echo "You answered no!"
else
   echo "You did not make a valid selection!"
fi
```


Yes this is perfect, thanks.

---

### Post by User3k on 2009-12-11
I am going to mark this as solved. Just found out the answer to my last question about executing another script is a yes.

---

