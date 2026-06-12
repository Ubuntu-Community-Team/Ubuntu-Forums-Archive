---
title: "Shell Script Problem"
date: 2010-08-17
forum: General Help
---

### Post by Guerreiro on 2010-08-17
Esteemed Linux users,

I need a small problem and I am not really sure this is the correct place or not. So please move or delete it if it is not correct.

I am with a small shell scripting problem. 

I want to feed multiple sites to host to get the IP address so I can know on which server it is so far I got this:

```
#!/bin/bash

echo "Please enter the site(s) you want to know the IP of:"
read site
echo "Please enter name of the file where you want to append the IP addresses to:"
read filename

host $site | grep address >> ./$filename
```

I would like to get multiple sites in to this, but I am afraid I would not know how.

---

### Post by Zorgoth on 2010-08-17
You could use a for loop, since website do not have spaces in their urls:

```

#!/bin/bash
echo "Please enter the site(s) you want to know the IP of:"
read sitelist
echo "Please enter name of the file where you want to append the IP addresses to:"
read filename
for site in ${sitelist}
do
    host $site | grep address >> ./$filename
done

```

The input is just a space-separated list of urls.

---

### Post by Guerreiro on 2010-08-17
> **Zorgoth said:**
> You could use a for loop, since website do not have spaces in their urls:

```

#!/bin/bash
echo "Please enter the site(s) you want to know the IP of:"
read sitelist
echo "Please enter name of the file where you want to append the IP addresses to:"
read filename
for site in ${sitelist}
do
    host $site | grep address >> ./$filename
done

```

The input is just a space-separated list of urls.

That simple? :O Wow, thank you very much. You made one aspect of my job a little easier again. :D

---

