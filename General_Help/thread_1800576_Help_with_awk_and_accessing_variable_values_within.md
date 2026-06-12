---
title: "Help with awk and accessing variable values within the syntax"
date: 2011-07-09
forum: General Help
---

### Post by meridionaljet on 2011-07-09
Hello,

I'm writing a bash script, and I am having trouble with this line:

awk '{print "url = \"http://www.example.com/directory/$type/"$1"\""}' input.file > output.file

Within the URL being printed, I wish the value of the variable "$type" to be printed. However, the quotation marks associated with the awk command do not allow the value of the variable to be called (syntax highlighting doesn't recognize $type as a variable, but rather as a literal part of the URL). Thus, the URL that ends up being printed literally has "$type" printed as a part of it. I would like to know how to change this behavior so that the actual value of the variable $type is printed within the URL instead. Any help would be appreciated.

---

### Post by Habitual on 2011-07-09
[http://www.unix.com/shell-programming-scripting/](http://www.unix.com/shell-programming-scripting/) has serious [gna]wk gurus.

---

### Post by gmargo on 2011-07-09
There are probably multiple ways to do this, but here's one, using **awk(1)**'s "-v" option:
```

$ type="one"
$ /bin/echo -e "foo\nbar" | awk -v TYPE=$type 'BEGIN{TypeVal=TYPE;OFS=""}  {print "url=\"http://www.example.com/directory/",TypeVal,"/",$1,"\""}'
url="http://www.example.com/directory/one/foo"
url="http://www.example.com/directory/one/bar"

```

---

### Post by meridionaljet on 2011-07-09
> **Habitual said:**
> [http://www.unix.com/shell-programming-scripting/](http://www.unix.com/shell-programming-scripting/) has serious [gna]wk gurus.

I followed your advice, and got a solution almost instantly lol.

Solution:

```
echo "enter the value of type"
read type
awk -v type=$type '{printf("url = \"http://www.example.com/directory/%s/%s/\"\n",type,$1)}' input.file > output.file
```

---

### Post by Habitual on 2011-07-09
ya, there are some serious lurkers there. :)

---

