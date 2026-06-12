---
title: "Webalizer and limiting to a certain subdirectory"
date: 2010-11-05
forum: General Help
---

### Post by fantastic on 2010-11-05
Trying to figure out how to configure Webalizer so that it only reports on 1 specific directory and its subdirectory contents.

Example:
[LIST]
[*]/Site Root
[LIST]
[*]/Dir1
[LIST]
[*]junk1
[*]junk2
[/LIST]
[/LIST]
[LIST]
[*]/Dir2
[LIST]
[*]junk3
[*]junk4
[/LIST]
[/LIST]
[LIST]
[*]/Dir3
[LIST]
[*]junk5
[*]junk6
[/LIST]
[LIST]
[*]/subDir3
[LIST]
[*]junk7
[/LIST]
[/LIST]
[/LIST]
[/LIST]

I'm trying to figure out how to only get the contents within Dir3. I tried the following but it did not work:
```
IncludeURL      /Dir3/*
IncludeURL      /Dir3*
```

I also added the following in conjunction with above, but it still did not work:
```
IgnoreSite      mysite.com/*
IgnoreSite      mysite.com*
```

How would it be configured?

Thanks in advance for any help.

---

### Post by fantastic on 2010-11-24
For those after me, I used to the following settings:

Set **Hostname**:

```
Hostname   /MyDir
```


Set AllSites and AllURLs:

```
AllSites   yes
AllURLs   yes
```


Block entire site:

```
HideSite   mydomain.com/*
```

Allow only your directories:

```
InlcudeURL /MyDir/*
```

IncludeURL is case-sensitive.


*I realize this is not how Webalizer was intended to be used.*

> # The Include* keywords allow you to force the inclusion of log records
# based on hostname, URL, user agent, referrer or username.  They take
# precidence over the Ignore* keywords.  Note: Using Ignore/Include
# combinations to selectivly process parts of a web site is _extremely
# inefficent_!!! Avoid doing so if possible (ie: grep the records to a
# seperate file if you really want that kind of report).

---

