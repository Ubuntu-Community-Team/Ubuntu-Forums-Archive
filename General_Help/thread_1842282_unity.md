---
title: "unity"
date: 2011-09-11
forum: General Help
---

### Post by raja.genupula on 2011-09-11
while writing a solution about a thread with unity problem 
i have seen the command as this 
```
unity --replace
``` 

i suggest him a command as ```
unity --reset
```

both things gave the same output . 
what is the necessity of the first command , because for the same output we no need to create two commands. there will be a difference between these two things . i am curious to know that .
& dont mind if it is a stupid issue or Question , just i wanna know .

---

### Post by VinDSL on 2011-09-11
I've used both commands, but it's been a while.

If I remember correctly, --replace simply restarts Unity.  You would do this after you've customized elements in the panel, for instance.

--reset restarts Unity also, but it resets everything back to the default configuration, so you lose any changes and customization that you've done.

---

### Post by howefield on 2011-09-11
> **VinDSL said:**
> If I remember correctly, --replace simply restarts Unity.  You would do this after you've customized elements in the panel, for instance.

--reset restarts Unity also, but it resets everything back to the default configuration, so you lose any changes and customization that you've done.

Spot on.

You wouldn't likely use --replace to fix a "broken" Unity.

---

### Post by raja.genupula on 2011-09-11
actually about this  i am talking 

[http://ubuntuforums.org/showthread.php?t=1841380](http://ubuntuforums.org/showthread.php?t=1841380)

---

### Post by Frogs Hair on 2011-09-11
This command is for icons .```
unity --reset-icons
```

---

### Post by cariboo on 2011-09-11
To the op, if you had opened a terminal and typed:

```
unity --help
```

you would have received the following response:

```
unity --help
Usage: unity [options]

Options:
  --version         show program's version number and exit
  -h, --help        show this help message and exit
  --advanced-debug  Run unity under debugging to help debugging an issue. /!\
                    Only if devs ask for it.
  --distro          Remove local build if present with default values to
                    return to the package value (this doesn't run unity and
                    need root access)
  --log=LOG         Store log under filename.
  --replace         Run unity /!\ This is for compatibility with other desktop
                    interfaces and acts the same as running unity without
                    --replace
  --reset           Reset the unity profile in compiz and restart it.
  --reset-icons     Reset the default launcher icon.
  -v, --verbose     Get additional debug output from unity.
```

---

### Post by raja.genupula on 2011-09-11
> **Frogs Hair said:**
> This command is for icons .```
unity --reset-icons
```

hey man 
thank you very much . but i know already . i am jut little but confuse about replace and reset . thanks for pick up .

---

### Post by raja.genupula on 2011-09-11
> **cariboo907 said:**
> To the op, if you had opened a terminal and typed:

```
unity --help
```

you would have received the following response:

```
unity --help
Usage: unity [options]

Options:
  --version         show program's version number and exit
  -h, --help        show this help message and exit
  --advanced-debug  Run unity under debugging to help debugging an issue. /!\
                    Only if devs ask for it.
  --distro          Remove local build if present with default values to
                    return to the package value (this doesn't run unity and
                    need root access)
  --log=LOG         Store log under filename.
  --replace         Run unity /!\ This is for compatibility with other desktop
                    interfaces and acts the same as running [B]unity without
                    --replace[/B]
  --reset           Reset the unity profile in compiz and restart it.
  --reset-icons     Reset the default launcher icon.
  -v, --verbose     Get additional debug output from unity.
```

ok , could you please explain me , (bold area i am not getting )

---

### Post by cariboo on 2011-09-11
> **raja.genupula said:**
> ok , could you please explain me , (bold area i am not getting )

You are focusing on the wrong part of the option:

```
--replace         Run unity
```

is what the option does, if you find the explanation of the option confusing, why not email the author and ask for clarification?

---

### Post by Krytarik on 2011-09-11
> **raja.genupula said:**
> ok , could you please explain me , (bold area i am not getting )
This means that this
```
unity --replace
```
does the same as this
```
unity
```
Supposedly, but didn't test it, obviously.

Greetings.

---

### Post by raja.genupula on 2011-09-12
> **cariboo907 said:**
> You are focusing on the wrong part of the option:

```
--replace         Run unity
```

is what the option does, if you find the explanation of the option confusing, why not email the author and ask for clarification?
hey cariboo907 thanks 
i do

---

### Post by raja.genupula on 2011-09-12
> **Krytarik said:**
> This means that this
```
unity --replace
```
does the same as this
```
unity
```
Supposedly, but didn't test it, obviously.

Greetings.

man i think unity command in terminal going to run another unity process . because i ran it . but running unity in terminal doesn't show you another unity . its takes you to same desktop but its not our original applet . when i close terminal which is running unity command , again its back to our desktop . 

this is what i have seen , thanks for suggesting me that .

---

### Post by raja.genupula on 2011-09-14
thanks to all who pick this thread .
thanks for your time .

---

