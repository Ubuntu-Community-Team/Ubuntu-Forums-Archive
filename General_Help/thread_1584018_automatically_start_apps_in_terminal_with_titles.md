---
title: "automatically start apps in terminal with titles?"
date: 2010-09-28
forum: General Help
---

### Post by tripzilch on 2010-09-28
Hi!

One of the first things I do when starting Ubuntu (Netbook Edition) is to open a Terminal (ctrl-alt-T) with three tabs in it (ctrl-shift-T, ctrl-shift-T), one with irssi, one with ipython and one extra with just the commandline. Then I set the titles (F2) of the first two respectively to "irssi" and "ipython".

Is there some way to write a script that automatically does all this? Or maybe save this configuration in a profile setting or something?

---

### Post by nothingspecial on 2010-10-01
Use screen, I think its installed by default

You need to make a .screenrc

```
nano ~/.screenrc
```Put this in it
```

screen -t irssi      0   irssi
screen -t ipython 1   ipython
```

*****EDIT** the forum is making my spacing wonky, but it doesn`t matter **Edit*****


It will give you a 3rd window anyway. The first instance of irssi on the line is the name of the widow, the second is the command to launch in that window, so if you put

```
screen -t bananas   0  irssi
```Then the window would be called bananas but irssi would still be launched in it.

The number is the window you want it to appear in, 0 first.

Launch screen, although you will probably find byobu (a pimped up version) easier.

```
byobu
```Go forward and back between the windows using F3 and F4 or create a new one with F2 (byobu only)

Or go to a specific one by pressing Ctrl A together then the number of the window (screen and byobu), so ctrl A then 0 for irssi, or Ctrl A then 1 for ipython

There are tons of other things you can do with screen/byobu

Detach and reattach sessions
Split windows
Use the same session on different computers
etc etc etc

Have you got irssi set up to autoconnect and identify you and what have you?

---

### Post by tripzilch on 2010-10-06
Heyy thanks! That was not *exactly* what I wanted to know, but byobu seems fancy enough (compared to screen) that I'm going to use that anyhow.

Though if anyone knows how to do it in Gnome Terminal, I'd still like to know, just for knowing it--waitaminute ... *lightbulb*

```
man gnome-terminal
```

ahhaaaaa ...

```
gnome-terminal --window -e "irssi" -t "irssi" --tab -e "ipython" -t "iPython" --tab
```

tadaaaah! ;-)

I dunno, for some reason I hadn't come up with the idea that the gnome terminal window is its own application with its own commandline (and not just bash), and then it was easy :)

Anyway, I'm going to try byobu for a while cause it looks neat, with the statusbar, just what I need so I don't get lost like in screen sometimes (which is why I use screen mainly for when I'm SSHing onto some server far away, to not lose my stuff when the connection drops). 
I suppose I can best run byobu in that special text-only screen I get when I do ctrl-alt-F2, right? Although I guess that means I can't plot graphs with pylab, but I have to start a new "ipython -pylab" for that anyway.

> **nothingspecial said:**
> Have you got irssi set up to autoconnect and identify you and what have you?

Yup, lots of that and what have you's :) Although I was kind of surprised that the irssi documentation/manual is unfinished. I thought irssi was like one of those ancient terminal applications that has been around forever (ok, just over two decades then) and reading ".. no, the docs end here, I got bored of writing these after a few days and  haven't touched these since then." on its homepage--where it says "IRC client of the future"--didn't expect that, for such a widely used program.

I also installed twirssi into irssi, so I use it to Twitter with. It's not perfect, but then, neither has any Twitter-client been for me so far, but this one has the bonus that I have been happily hacking away at the twirssi perl sourcecode :-) I want to make it so that I can add extra rules to the subscribed searches depending on username and regexes. Cause I find it most useful to subscribe to #nameofmyhometown, provides me with lots of useful local information, gossip and chatter. Except unfortunately there are also a bunch of real estate twitterers and like five different accounts that immediately retweet whatever news appears on the local city newspaper sites when I only need it once, and even then I need a regex filter for /old (lady|man) (falls from|gets hit by) (bike|bus|motor)/ :-P As well I need to figure out how to sort that stuff into different irssi windows ... so much to learn :) And it gives me an excuse to sharpen my perl skills as well!

---

### Post by nothingspecial on 2010-10-06
You could try bitlbee in irssi, that does twitter and google talk and other chat things.

I`ve never used twirssi, but maybe /ignore would work for tweets.

---

