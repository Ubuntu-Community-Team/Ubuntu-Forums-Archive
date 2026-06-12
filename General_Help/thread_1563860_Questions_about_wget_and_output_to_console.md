---
title: "Questions about wget and output to console"
date: 2010-08-29
forum: General Help
---

### Post by Volt9000 on 2010-08-29
This is really bugging me.

Recently I saw someone's conkyrc which fetches their external IP with the following simple bash command:

```

wget http://www.whatismyip.org -O - | tail

```

I looked at this and thought "Hmm, why do they need to pipe the output through tail?" Well, I removed that, and got no output from the page!
Here's what I get:

```

--2010-08-29 18:46:47--  http://www.whatismyip.org/
Resolving www.whatismyip.org... 98.207.226.113
Connecting to www.whatismyip.org|98.207.226.113|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `STDOUT'

    [<=>                                                                                                                    ] 0           --.-K/s              1    [ <=>                                                                                                                   ] 14          --.-K/s   in 0.001s  

2010-08-29 18:46:47 (22.7 KB/s) - written to stdout [14]

```

It says it wrote 14 bytes to stdout, but I don't see my IP there. I started playing around with output redirects, and this seemed to work:

```

wget http://www.whatismyip.org -O - 2> -

```

With this, I see ONLY the IP address. So my question is, why is the IP being output on stderr instead of stdout? And if this is the case, why does this work? tail shouldn't be able to read from stderr, should it?

---

### Post by lloyd_b on 2010-08-30
I don't entirely understand this one.  The information *is* being put on stdout.  For example:```
wget http://www.whatismyip.org -O - | cat
``` would display nothing if the data wasn't on stdout, but it does display the IP address.

That person is using 'tail' for the same reason I use 'cat' - to actually get the IP address to display.

My only guess - stdout is buffered, and as such nothing sent to it will be displayed until a newline is sent.  Maybe wget is somehow clearing the stdout buffer without the newline being sent?  Or maybe stderr is "stomping on" the text is the display buffer?

FYI - ```
wget http://www.whatismyip.org -O - 2> -
``` isn't doing what you think it's doing.  Specifically, it's creating a file named "-", and redirecting stderr (which include most of wget's output) into that file.  Do a 'ls' on the current directory, and you should see that file (if you want to display or delete it, use "./-" instead of "-", to avoid confusing the shell).

Lloyd B.

---

### Post by Volt9000 on 2010-08-30
Thanks for the reply.

I think you're right about the buffered stdout and newline, because when the IP displays, the prompt appears right after, on the same line.

And thanks for the heads up about the '-' file, I did indeed find it. :)

---

