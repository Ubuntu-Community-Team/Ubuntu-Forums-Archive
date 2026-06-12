---
title: "Deleting multiple lines with sed."
date: 2012-01-25
forum: General Help
---

### Post by morle on 2012-01-25
Hi,

I want to delete various lines from a file if they have any word from a list of words, ie: apple and lemon.

However, I only could call sed with one word at a time:
[LEFT][I]sed '/apple/d' file > file2
sed '/lemon/d' file2 > file3

[/I]Is there a way to do both at once?

Thanks!
[/LEFT]

---

### Post by erind on 2012-01-25
**grep** has **--file** option, that might be helpful:

 ```
grep -v --file=list filename
```Where **list **is the file that has your words, one per line. 

```
$ cat list
apple
lemon
orange
```Make sure there are no _empty_ lines in the list file.

---

### Post by Telengard C64 on 2012-01-25
GNU Sed supports alternation as an extension.

```

sed '/apple\|lemon/d'

```

**_EDIT_**
This may help you understand.

[http://www.scootersoftware.com/RegEx.html](http://www.scootersoftware.com/RegEx.html)

---

### Post by dcstar on 2012-01-25
How to pick if someone asking for help with their homework/assignment:
[LIST=1]
[*]Their Ubuntu post count is (usually) very low.
[*]The question they are asking is usually a very basic command line task.
[*]Many similar posts appear in the forums at the same time.
[/LIST]
[SIZE="3"]Stop helping these bludgers![/SIZE]

---

### Post by morle on 2012-01-26
Hi,
[LEFT]thanks to everyone, except __dcstar. Sorry to mess up your revelations, but it's been years since I had homework/assignments. It is simply that I'm trying to understand how this sed thing works.

Thanks.
[/LEFT]

---

