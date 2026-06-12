---
title: "Help with alias and variables"
date: 2009-09-10
forum: General Help
---

### Post by Conlin94 on 2009-09-10
I want to make a command that allows me to type "google {texthere}" and it will put text as the query. I already have and alias like this:

alias google=curl -A Mozilla http://www.google.com/search?q={texthere}  |html2text -width 70

and I want the {texthere} to be the  text that I type after google. Does this make sense?

---

### Post by mbrush on 2009-09-10
Make a new file and make it executable:
```

cd ~
touch google
chmod +x google

```

Then put this content into it and try it out:

```

#!/usr/bin/env bash
curl -A Mozilla "http://www.google.com/search?q=${1}" | \
html2text -width 70

```

Then run it:
```

./google "Some search string"

```
If it runs properly, you can move it into somewhere in your path, for example:
```

cp ~/google /usr/bin/

```
The you can run it from any directory, like:
```

google "Some search string"

```
I'm not sure if this is what you are wanting?

Good luck

---

### Post by kaibob on 2009-09-10
I believe you have to use a function in the .bashrc file. For example,

```
edit () {
gedit "$1"
}
```

You would then type edit followed by the filename to open the file in gedit.

---

### Post by jpkotta on 2009-09-10
> **kaibob said:**
> I believe you have to use a function in the .bashrc file. For example,

```
edit () {
gedit "$1"
}
```

You would then type edit followed by the filename to open the file in gedit.

Yes, I would use a function.

```

function google()
{
    if [ -z "$1" ] ; then 
        echo "Usage: google querystring"
        return
    fi
    curl -A Mozilla "http://www.google.com/search?q=${1}" \
        | html2text -width 70 | less;
}

```

---

