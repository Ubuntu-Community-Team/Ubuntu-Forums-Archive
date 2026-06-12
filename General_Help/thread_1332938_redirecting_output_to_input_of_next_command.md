---
title: "redirecting output to input of next command"
date: 2009-11-20
forum: General Help
---

### Post by mo.reina on 2009-11-20
i'm trying to redirect the output of a command to the input of the next command.  not sure if i'm going about this the right way.  an easy method would be just to store the output of the previous command in a file and redirect input to read that file, but i'm curious to see if this can be done without writing to any files.

my code:
```
exec 7<&0
df <&1 | grep sda1 | awk '{ print $3, $4 }'
read used free

```

---

### Post by lavinog on 2009-11-20
like this:
```
df | grep sda1 | awk '{ print $3, $4 }'
```

---

### Post by mo.reina on 2009-11-20
```
df | grep sda1 | awk '{ print $3, $4 }'
```
will output 2 variables, which i'm trying to use as input for the read command.

the smart way to do this would probably be

```

df | grep sda1 | awk '{ print $3, $4 }' > file
exec < file
read used free

```

but i'm trying to do this without redirecting to a file, basically trying to catch the output of awk and pipe it into the read command.  i think the problem is inheritance between the child and parent processes.

---

### Post by kaibob on 2009-11-21
I've just been reading about process substitution and wondered if this might be an instance where process substitution could be used?

For example:

```
read used free < <(df | grep sda1 | awk '{ print $3, $4 }')
```

It seems to work:

> $ df | grep sda1 | awk '{ print $3, $4 }'
2855260 23362784

$ read used free < <(df | grep sda1 | awk '{ print $3, $4 }') ; echo $used
2855260

$ read used free < <(df | grep sda1 | awk '{ print $3, $4 }') ; echo $free
23362784

read used free < <(df | grep sda1 | awk '{ print $3, $4 }') ; echo $used $free
2855260 23362784




---

### Post by lavinog on 2009-11-21
you could also store it in a variable, then split that variable up.
```

dfstr=$(df | grep sda1)
used=$(echo $dfstr | awk '{ print $3 }')
free=$(echo $dfstr | awk '{ print $4 }')
echo "Used: $used"
echo "Free: $free"

```

---

### Post by mo.reina on 2009-11-21
> **kaibob said:**
> I've just been reading about process substitution and wondered if this might be an instance where process substitution could be used?

For example:

```
read used free < <(df | grep sda1 | awk '{ print $3, $4 }')
```

It seems to work:

hey that's looks like the thing i've been looking for.  why the two "**< <**" instead of:

```
read used free <(df | grep sda1 | awk '{ print $3, $4 }')
```

another solution that was presented on another linux forum was to use an array to store the variables, which is also ok, but not really what i was looking for.  i was specifically trying to find a way to redirect the STDOUT and STDIN directly, without passing STDOUT to files, variables, etc.

```
line=($(df|grep sda1))
used=${line[2]}
free=${line[3]}
```

interestingly enough, there is a command called **line**, which takes the first line of STDIN and passes it to STDOUT.  has anyone had any experience with it?

---

### Post by kaibob on 2009-11-21
> **mo.reina said:**
> why the two "**< <**" instead of:

```
read used free <(df | grep sda1 | awk '{ print $3, $4 }')
```

I'm just learning process substitution, so I'm not certain of the answer to this question. But, I'll give it a try and more knowledgeable forum members can correct what I get wrong. 

As I understand things, process substitution creates a temporary file, which, by itself, does nothing. So, in this instance, the temporary file created by process substitution needs to be redirected to the read command, which is the reason for the second '<'. If this is correct, 'file' and '<(commands)' are, in a sense, functionally equivalent in the following command lines. 

```
read var1 var2 < file

read var1 var2 < <(commands)
```

---

### Post by mightymouse2045 on 2011-07-02
> **mo.reina said:**
> hey that's looks like the thing i've been looking for.  why the two "**< <**" instead of:

```
read used free <(df | grep sda1 | awk '{ print $3, $4 }')
```another solution that was presented on another linux forum was to use an array to store the variables, which is also ok, but not really what i was looking for.  i was specifically trying to find a way to redirect the STDOUT and STDIN directly, without passing STDOUT to files, variables, etc.

```
line=($(df|grep sda1))
used=${line[2]}
free=${line[3]}
```interestingly enough, there is a command called **line**, which takes the first line of STDIN and passes it to STDOUT.  has anyone had any experience with it?


Hi - I know this post is marked as solved but hoping someone could help me to do the same. But it's a command from Fedora so hopefully no one spits the dummy.

I want to run this command

gsettings list-schemas

and redirect the out put to this command

gsettings list-recursively

The first command returns a list of names with a space separating each one. But when I have tried your examples here it seems to be piping the whole output in one go and therefore failing...

---

