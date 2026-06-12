---
title: "Printf output can be deleted by user"
date: 2011-11-08
forum: General Help
---

### Post by J0hnnyBr@v0 on 2011-11-08
I wrote a bash script that outputs a line and then reads input from a user and assigns it to a variable.

What I have noticed is if I start to enter the input and then press delete, the entire printf string gets deleted.

Ex:
Please enter your name: Eric

If I delete the 'E' in Eric, the "Please enter your name:" portion also disappears.

Is there a way to prevent that from happening? Here is my code:

printf "Please enter your name: "
read -e $NAME

Thanks in advance

---

### Post by WorMzy on 2011-11-08
Doesn't happen to me in urxvt. It may depend on which terminal emulator you're using.

Try adding a linebreak to the end of the printf statement:

```
printf "Please enter your name:\n"
```

---

### Post by J0hnnyBr@v0 on 2011-11-08
Yeah, but that puts the input on a new line. I don't want it on a new line. I want it inline.

Any other thoughts?

---

### Post by Slim Odds on 2011-11-08
> **J0hnnyBr@v0 said:**
> Yeah, but that puts the input on a new line. I don't want it on a new line. I want it inline.

Any other thoughts?

My thought is that writing user interactive programs in a bash shell is pretty crude. If you want a more sophisticated system, you'll need to move into some other programming environment.

---

### Post by WorMzy on 2011-11-08
After experimentation, it appears that I can replicate the behaviour in bash, when it pretends to be sh. Neither bash nor zsh behave the same way, so if you're using bash as sh, try just using bash, or maybe dash.

---

### Post by J0hnnyBr@v0 on 2011-11-08
Yeah...unfortunately all I know is Bash...and not so good at that either ;)

I was hoping there would be a workaround, but I haven't found one yet...

Thanks for your reply.

---

### Post by AnojiRox on 2012-03-10
i don't know much about printf; but this works in bash:
```
echo -n 'please enter your name: ';read name
```

---

