---
title: "bash script oddity?"
date: 2010-01-26
forum: General Help
---

### Post by Mb0742 on 2010-01-26
```

#bin/bash
a=$(curl "http://www.samair.ru/proxy/proxy-01.htm" | grep -o "[a-z]=[0-9]")
echo $a | le=(`grep -o "[a-z]"`)
echo $a | nu=(`grep -o "[0-9]"`)
echo ${nu[2]}

```

no matter what I do I can't get this to work, help pleeeease?

---

### Post by t4thfavor on 2010-01-26
Explain what you want to do maybe, and you will get more posts.

I can give it a try if you tell me your desired outcome.

---

### Post by Mb0742 on 2010-01-26
The script is to interpret a proxy list website, while originally it worked without flaw, the website began seeding their port numbers with javascript variables.

The allocation for each number / letter encryption is coded like follows:

x=1
b=5
etc.

What I am trying to do is allocate the grep'd string into the variable 'a', then write it into 'le' for letter (an array) and nu (an array) so that I can unseed the port and verify the proxy.

Hope this helps.

**Edit**:
Hurrr forgot to put the main variable inside the command that defines the array...

```

#bin/bash
a=$(curl "http://www.samair.ru/proxy/proxy-01.htm" | grep -o "[a-z]=[0-9]")
le=(`echo $a | grep -o "[a-z]"`)
nu=(`echo $a | grep -o "[0-9]"`)
echo ${nu[2]}


```

---

### Post by t4thfavor on 2010-01-26
I believe this is what your after.

```

#bin/bash
a=`curl "http://www.samair.ru/proxy/proxy-01.htm" | grep -o "[a-z]=[0-9]"`;

le=$(echo $a |grep -o "[a-z]");

nu=$(echo $a |grep -o "[0-9]");

e=$(echo $nu | sed 's/\(.\)/\1 /g')
str=($e)

#echo "e = \"$e\""

#echo "str[*] = \"${str[*]}\""
#for i in $(seq 0 $((${#str[*]} - 1))); do
#       echo "str[$i] = \"${str[$i]}\""
#done
echo ${str[2]}


```

In the original version nu was a string, not an array of chars. I fixed it with some sed action. the output is a single '0'. If you uncomment the loop. it prints a whole mess of numbers.

---

