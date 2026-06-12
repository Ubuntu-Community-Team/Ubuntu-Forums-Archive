---
title: "conky if_match problem"
date: 2011-02-08
forum: General Help
---

### Post by marcosx2 on 2011-02-08
Hello there,

I have line in my conky.conf:

```
${color white}${if_match ${fs_used_perc /}>=90}${color red}${endif}${fs_free /}
```

Works perfectly. If free space is less than 90% then conky write amount of space in red color. Now, how to change expression to have amount of space in GiB/MiB?

```
${color white}${if_match ${fs_used /}>=2GiB}${color red}${endif}${fs_free /}
```

This not working, I have :"compare failed for expression" '10.5GiB>2GiB, even if I use " " signs.

also, if amount of free space is less than 1GiB, ex. 0.98 MiB - how to create function to compare?

Thanks for help.

---

### Post by stinkeye on 2011-02-08
I don't think the if_match statement will work with **>=** unless the output/input
is just a number.

---

### Post by Habitual on 2011-02-08
Here's another example:
```

${if_match ${wireless_link_qual wlan0} < 31}${color orange}bad$color$else${if_match ${wireless_link_qual wlan0} < 51}${color yellow}weak
```

Here's an actual that I used in my portmon widget:
```
${if_match ${tcp_portmon 1 65535 lport 0}<=32767}${color blue}${endif}
```

Here's what the [man page]("http://conky.sourceforge.net/docs.html") says about it:
if_match expression
    Evaluates the given boolean expression, printing everything between $if_match and the matching $endif depending on whether the evaluation returns true or not. Valid expressions consist of a left side, an operator and a right side. Left and right sides are being parsed for contained text objects before evaluation. Recognised left and right side types are:
    doubleArgument consists of only digits and a single dot.
    longArgument consists of only digits.
    stringArgument is enclosed in quotation marks (")
    Valid operands are: '>', '<', '>=', '<=', '==', '!='.

HTH.

Other example may exist at [The Conky Pitstop]("http://conky-pitstop.wikidot.com/")

---

### Post by marcosx2 on 2011-02-08
fs_free give you for example output like this: 2.56GiB also 450MiB if you have less than 1GB free space.



ok I made something like this:

```

${color white}
${if_match "${fs_free /}"<"2GiB"}${color red}
${else}
${if_match "${fs_free /}"<"999MiB"}$color red}
${endif}
${fs_free /}

```

Now I test this is working or not.

---

