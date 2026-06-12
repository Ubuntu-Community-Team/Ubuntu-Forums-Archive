---
title: "Need help with alias command"
date: 2009-09-29
forum: General Help
---

### Post by wavesailor on 2009-09-29
Hi All,

I found this great site [http://nodeone.se/blogg/tips/shell-aliases-make-drupal-administration-easier#wtar]("http://nodeone.se/blogg/tips/shell-aliases-make-drupal-administration-easier#wtar") with some neat alias examples.

The one I'm trying to get to work is the wtar example. It does a wget and then untars it but for the life of me I'm cannot get it to work??
```
# Download tarball and unpack it.
wtar () { wget -q -O - $1 | tar zxv --no-same-owner --no-same-permission ; }

```


When I add that to my ~/.bash_aliases file it does not show up in the alias. 

I then tried my own variation:
```
alias wtar='wget -q -O - $1 | tar zxv --no-same-owner --no-same-permission'

```
but that gives thisd error 
```
gzip: stdin: not in gzip format
tar: Child returned status 1
```

Any ideas or bash experts who can help me please?


-jj

---

### Post by StuartN on 2009-09-29
> **wavesailor said:**
> wtar () { wget -q -O - $1 | tar zxv --no-same-owner --no-same-permission ; }[/CODE]

This first one is not an alias but a function, so it does not show up in the output of alias. After defining this function you can type **wtar [http://somefile.zip](http://somefile.zip)** and it should work, so long as no other wtar is defined or aliased.

I would try **alias wtar='wget -q -O - $1'** first, and see what happens with a (small) download, then add **| tar** once you are sure it works.

---

### Post by wavesailor on 2009-09-30
After your response, I re-added it to my .bash_alias file and **it worked** :-)
Strange - I must have initially made a typo. Thanks for pointing out that "functions" do not show up in the output of alias. Just curious if there is a way to output them?

I one thing that I did notice is that if I do a **sudo wtar _[http://somefile.zip](http://somefile.zip)_** I get "command not found" - I'm guessing that I would have to put the wtar function into root's .bash_alias file - is that correct?

---

### Post by nikhilk on 2009-09-30
> **wavesailor said:**
> I one thing that I did notice is that if I do a **sudo wtar _[http://somefile.zip](http://somefile.zip)_** I get "command not found" - I'm guessing that I would have to put the wtar function into root's .bash_alias file - is that correct?

Yes, that is correct. But you probably would never need it, why to download something as root right?

---

### Post by StuartN on 2009-09-30
> **wavesailor said:**
> "functions" do not show up in the output of alias. Just curious if there is a way to output them?

Yes, **declare -F** will list the names of every function that has been declared, while **declare -f** lists both the name and definition. This can be limited to a single declaration, e.g. **declare -f my_func**.

The manual page for declare is missing but it can be found as the first Google result for "man declare" (which surprised me, because men do a lot of kinds of declaring!).

---

### Post by wavesailor on 2009-09-30
Thanks **All** for the valuable help - Much appreciated :-)

---

### Post by Dougie187 on 2009-09-30
```
alias wtar='wget -q -O - $1 | tar zxv --no-same-owner --no-same-permission'
```

In this your typo would depend on what you were downloading with wget. This tar assumes you are downloading a .tar.gz or .tgz file. If you are only downloading a .tar then it would look like this.

```
alias wtar='wget -q -O - $1 | tar xv --no-same-owner --no-same-permission'
```

---

