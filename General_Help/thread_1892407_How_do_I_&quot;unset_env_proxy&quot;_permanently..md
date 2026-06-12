---
title: "How do I &quot;unset env proxy&quot; permanently."
date: 2011-12-07
forum: General Help
---

### Post by KebertX on 2011-12-07
I just have a minor annoyance I thought I could ask for advice on.

When I open terminal, whenever I try something like wget, apt-get, or anything that requires internet access, it will tell me "Error: Connection refused"

I know the problem and have a half-assed solution.
```
me@MyComputer:~$ env | grep proxy
http_proxy=http://127.0.0.1:4444/
https_proxy=https://127.0.0.1:4445/
```
It's automatically using i2p proxy settings. All I have to do is type
```
unset http_proxy
unset https_proxy
```
And then it works again. Until I close terminal. The original proxy settings are restored every time.

That is really annoying. A wise man once said, Where there's a shell, there's a way. This is probably easy, so please do chime in! What do I do?

---

### Post by josephmills on 2011-12-07
> **KebertX said:**
> I just have a minor annoyance I thought I could ask for advice on.

When I open terminal, whenever I try something like wget, apt-get, or anything that requires internet access, it will tell me "Error: Connection refused"

I know the problem and have a half-assed solution.
```
me@MyComputer:~$ env | grep proxy
http_proxy=http://127.0.0.1:4444/
https_proxy=https://127.0.0.1:4445/
```
It's automatically using i2p proxy settings. All I have to do is type
```
unset http_proxy
unset https_proxy
```
And then it works again. Until I close terminal. The original proxy settings are restored every time.

That is really annoying. A wise man once said, Where there's a shell, there's a way. This is probably easy, so please do chime in! What do I do?


there is a great thing called alias that you put into your .bashrc
file you can find out  more about this here
**Types of Commands**
Aliases: Aliases are a way of shortening commands. They are only used in interactive shells, not in scripts. (This is one of the very few differences between a script and an interactive shell.) An alias is a name that is mapped to a certain string. Whenever that name is used as a command name, it is replaced by the string before executing the command. So, instead of executing:```

  $ nmap -P0 -A --osscan_limit 192.168.0.1
```
You could use an alias like this:```

  $ alias nmapp='nmap -P0 -A --osscan_limit'
  $ nmapp 192.168.0.1
```
Aliases are limited in power; the replacement only happens in the first word. If you want more flexibility, use a function. Aliases are only useful as simple textual shortcuts.

 Please see [http://mywiki.wooledge.org/BashGuide/CommandsAndArguments](http://mywiki.wooledge.org/BashGuide/CommandsAndArguments)

---

