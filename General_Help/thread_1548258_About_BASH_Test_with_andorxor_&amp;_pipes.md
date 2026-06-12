---
title: "About BASH: Test with and/or/xor &amp; pipes"
date: 2010-08-08
forum: General Help
---

### Post by smeagol271006 on 2010-08-08
Hi everybody.

I'm trying to work something for testing based on a relative filename the ../ or ./ of a directory:

example

```

test \(echo '../'| grep -q '^\.\{1,1\}'\) -a \(echo '../ | grep -q '^\.\{2,2\}'\)

```would give true

```

test \(echo './'| grep -q '^\.\{1,1\}'\) -a \(echo './ | grep -q '^\.\{2,2\}'\)

```and this one would give false

For example if you issue 

```
echo '../'| grep '^\.\{1,1\}'
```**.**./ (two dots, and the first dot matched by grep)

if you issue 

```
echo './'| grep '^\.\{2,2\}'
```will not match the two points at the beginning
Other alternative way

```
[ echo '../'| grep -q '^\.\{1,1\} ] && [ echo '../'| grep -q '^\.\{2,2\} ]  && echo true
```errors are:

```
bash: [: missing `]'
grep: [ ó ^[ desemparejados

```Notice I'm using the -q option to avoid output of grep. Logic would be applied based on exit status of grep of course.

Anyone would be so kind to tell me what I'm doing wrong (i guess the problem is with the pipes).

I also can stop whining, save the exit status on variables and later make a variable comparison (that is my last resort)?

A B A&B
0 0 0
0 1 0
1 0 0
1 1 1

[http://www.gnu.org/software/bash/manual/bashref.html#Shell-Expansions](http://www.gnu.org/software/bash/manual/bashref.html#Shell-Expansions)

I'm using this guides:
[http://tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html#sect_07_01_02_01](http://tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html#sect_07_01_02_01)
[http://tldp.org/LDP/abs/html/ops.html](http://tldp.org/LDP/abs/html/ops.html)

I'm no programmer and just a beginner ...
Not much experience in this.

Thanks in advance

---

### Post by dino99 on 2010-08-08
have a look there:

[http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)

---

### Post by DaithiF on 2010-08-08
Hi,
I'm not sure I've understood your question fully, but try this:
```
x="../"
[[ "$x" =~ "." && "$x" =~ ".." ]] && echo true || echo false
true
x="./"
[[ "$x" =~ "." && "$x" =~ ".." ]] && echo true || echo false
false


```

---

### Post by smeagol271006 on 2010-08-08
Thanks! I understood it. Very clear example. Had to read some references :P

I will read Mendel Cooper's guide to understand better these things. But first will finish with Machtelt Garrels one

[http://tldp.org/guides.html](http://tldp.org/guides.html)

Still, I should make the piped commands save their contents in variables. Not a good thing to do everything in a command ...

Here the version 3 of bash remarks:

[http://tldp.org/LDP/abs/html/bashver3.html](http://tldp.org/LDP/abs/html/bashver3.html)

---

