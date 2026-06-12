---
title: "Bash ALIAS Syntax Error - but the Command Works Fine in Terminal!"
date: 2009-08-27
forum: General Help
---

### Post by OzzyFrank on 2009-08-27
Hi. I made an **alias** for a rather long command string featuring the **[COLOR="DarkRed"]DU[/COLOR]** command, which _works absolutely fine in the terminal_, but apparently one of the characters makes it _invalid as an alias_. At least I know why half of my aliases were no longer working (anything below the offending line was ignored, or not processed).

So here is the command:

**[COLOR="Blue"]du -b --max-depth 1 | sort -nr | perl -pe 's{([0-9]+)}{sprintf "%.1f%s", $1>=2**30? ($1/2**30, "G"): $1>=2**20? ($1/2**20, "M"): $1>=2**10? ($1/2**10, "K"): ($1, "")}e'[/COLOR]**

And here is the error message (which is displayed as soon as I open a terminal):

**[COLOR="Indigo"]bash: /home/ozzman/.bash_aliases: line 21: syntax error near unexpected token `('[/COLOR]**

At first I thought it was talking about the single quote on the end (since, when adding aliases, you have to enclose the commands in single quotes) but then saw it was actally complaining about a **[COLOR="Blue"]([/COLOR]**.

Like I said, the command works fine, but I can't get this to be an alias. Any help would be appreciated. Thanks

---

### Post by Brandon Williams on 2009-08-27
> **OzzyFrank said:**
> So here is the command:

**[COLOR="Blue"]du -b --max-depth 1 | sort -nr | perl -pe 's{([0-9]+)}{sprintf "%.1f%s", $1>=2**30? ($1/2**30, "G"): $1>=2**20? ($1/2**20, "M"): $1>=2**10? ($1/2**10, "K"): ($1, "")}e'[/COLOR]**

With a command this complicated, it can be difficult to get the quoting and escapes right. My guess is that you got something just a little bit off when you declared the alias, and that this resulted in a '(' being unquoted.

The alias declare should look something like this:
```
alias foo='du -b --max-depth 1 | sort -nr | perl -pe '\''s{([0-9]+)}{sprintf "%.1f%s", $1>=2**30? ($1/2**30, "G"): $1>=2**20? ($1/2**20, "M"): $1>=2**10? ($1/2**10, "K"): ($1, "")}e'\'
```

---

### Post by OzzyFrank on 2009-08-30
I actually just copied the command as-is from the terminal (where it worked absolutely fine) into my alias file. So while it isn't due to any error on my part (I just copied it from a site), I had no doubt the complex nature of the command had something to do with it.

A point of interest: I went to a friend's place and wanted to show the command off, and in the terminal there it didn't work, but instead presented the same **'('** error! While this was straight in the terminal (which works fine here), I suppose I should point out for some reason his alias file is not working at all, which is something I'll have to look into. Don't know if that's related, but he got that error in the terminal, while I don't.

Just checked out the revised alias command, and it works fine, so thanks. I have to chop off some of the end characters to get it to work in the terminal, but the main point is I can apply a nice short alias to perhaps the longest command I have personally come across. Cheers.

---

