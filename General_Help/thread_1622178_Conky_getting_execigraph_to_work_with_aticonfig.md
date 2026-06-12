---
title: "Conky: getting execigraph to work with aticonfig"
date: 2010-11-15
forum: General Help
---

### Post by guildofghostwriters on 2010-11-15
Trying to get execigraph to work with aticonfig in conky.

The following line works after a fashion, displaying the number & % symbol:

```
${execi 10 aticonfig --adapter=0 --odgc | grep "GPU load" | cut -c32-34}
```

but the following displays either a static vertical line on the right edge of my conky or nothing at all:

```
${execigraph 10 aticonfig --adapter=0 ---odgc | grep "GPU load" | cut -c32-33}
```

I've tried tinkering with default_graph_size, with ""s around the aticonfig etc part, with the -c values in cut, have googled to the point of despair & tried various lines using tail or gawk (I don't have a clue about these, even after trying to read up, so tinkering with the values has been fruitless guesswork) that I found in forums. Nothing works. I think the main problem is that sometimes the result of aticonfig etc is a number between 0 & 99 which execigraph requires but if the gpu load is <10 then the result is a number and the % symbol. But this might be completely wrong because even when the load is >10, there's no graph.

Does anybody have any ideas? I was wondering if there was a way of using grep/cut/tail/gawk to ensure that the result was always a number? Thanks in advance for all suggestions!

---

### Post by guildofghostwriters on 2010-11-15
Ok, doing a bit more searching I discovered that I can use tr -d % to get rid of the percentage symbol. I also spotted the ---odgc typo in the code above. aticonfig --adapter=0 --odgc | grep "GPU load" | cut -c32-34 | tr -d % in the terminal shows the current gpu load as a number but does nothing with execigraph in conky.

---

### Post by guildofghostwriters on 2010-11-16
I'm guessing nobody has replied because nobody knows but I'll bump it this once anyway...

---

### Post by stinkeye on 2010-11-16
Can you get execibar to work?
I've tried execigraph with my nvidia card but I can't get it to work.
Execibar works though.

Try this thread where all the conky gurus hang out.
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=281865&page=1477[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865&page=1477")

---

### Post by guildofghostwriters on 2010-11-16
I thought I had tried execibar and it had worked but I just tried it again now & it doesn't. Hey ho!

---

### Post by stinkeye on 2010-11-16
If I use execbar (not execibar) and use **update_interval 1.0** in my
conky config and then run glxgears it shows around 60%.

---

### Post by guildofghostwriters on 2010-11-16
Thanks - still no joy though - made the changes you suggested and swirled a wobbly window around my desktop for a minute - the figure from the execi line went up but the bar is just a tiny vertical line on the rightmost edge that doesn't change. I also tried it with execgraph just to see and that's slightly different - just a blankspace when the load is 0 but as it goes up, a vertical line appears, about 30 pixels long, pushing the conky below it down, and then disappears even while the load is still high. I've made a support request on sourceforge so fingers crossed that works.

I like those cpu/gpu icons in your conky - where'd you get them?

---

### Post by stinkeye on 2010-11-16
There are settings to determine the graph sizes you put in you config.
From **man conky** ...
```
default_bar_size 
Specify a default width and height for bars. Example: 'default_bar_size 0 6'. This is particularly useful for execbar and execibar as they do not take size arguments.

default_graph_size 
Specify a default width and height for graphs. Example: 'default_graph_size 0 25'. This is particularly useful for execgraph and execigraph as they do not take size arguments
```
Don't know if that may make a difference.

eg for my execbar I use
```
${execbar nvidia-smi -a | grep -A 2 "Utilization" | tr -d % | grep "GPU" | awk '{print $3}'}
```


with a line in the config above "TEXT"
```
default_bar_size 80 10
```

---

### Post by guildofghostwriters on 2010-11-17
Thanks, I've got that set though, took me a while to figure it out because it's x y whereas the ***bar etc after TEXT are y,x. I should probably have posted my conky so you could see but the relevant bit is in a script (Someone on the conky irc thingy told me to try that when I looked for help there) so it was easier just to paste the lines in. Ta for trying!

---

