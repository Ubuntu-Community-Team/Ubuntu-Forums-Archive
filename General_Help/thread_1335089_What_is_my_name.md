---
title: "What is my name?"
date: 2009-11-23
forum: General Help
---

### Post by prc320 on 2009-11-23
Hi

What is my name

[email]symsr3@xxxxxx.xxx[/email]

The second and third bits please?

Robert

---

### Post by emigrant on 2009-11-23
what is this about? :confused:

---

### Post by prc320 on 2009-11-23
I stumbled over what my "name" is, how do I get the system to say what it is?

symsr is the computer name

*@* is @

*xxxxx* is what?

*xxx*  is what?

I hope that helps!

Robert

---

### Post by prshah on 2009-11-23
> **prc320 said:**
> 
[email]symsr3@xxxxxx.xxx[/email]

If you mean what is your *hostname* you can find it with the terminal (Applications-Accessories-Terminal) command```
hostname
```

---

### Post by wojox on 2009-11-23
[email]symsr3@ubuntu.com[/email]

---

### Post by t0p on 2009-11-23
> **prc320 said:**
> I stumbled over what my "name" is, how do I get the system to say what it is?

symsr is the computer name

*@* is @

*xxxxx* is what?

*xxx*  is what?

I hope that helps!

Robert

I think you mean you want to know what your user name is.   (that'll be *xxxx@symsr* (there's no *xxxxx.xxx*).

Open a terminal.  Look at the prompt.  Does it say *something@symsr*?  Well, that "something" is your user name.  If the prompt doesn't say anything like that, type into the terminal:

```
who
```

The output should include your user name.

---

### Post by reeboker on 2009-11-23
Or if you mean your username here on the forums, in my language prc=fart. :)

---

### Post by prc320 on 2009-11-23
Thanks everyone!

---

### Post by SPr on 2009-11-23
```

whoami

```
will show the user name.
```

sudo whoami

```
will always be root unless the OS has had a nervous breakdown.

---

### Post by slakkie on 2009-11-23
```

echo $USER@$(hostname)

```

---

