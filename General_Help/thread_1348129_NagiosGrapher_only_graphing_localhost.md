---
title: "NagiosGrapher only graphing localhost"
date: 2009-12-06
forum: General Help
---

### Post by Dr. Dom on 2009-12-06
Hi Guys,

I've recently installed the NagiosGrapher 1.7.1 following the instructions from the nagioswiki howto:
[http://www.nagioswiki.org/wiki/HowTos:BestPractice:NagiosGrapher](http://www.nagioswiki.org/wiki/HowTos:BestPractice:NagiosGrapher)

I have made changes to the configuration as instructed to the best of my abilities but I have no idea what this means and may be my issue:

*[COLOR="DarkOrange"]Change the graph_log_regex to match values in the Nagios Status Output (the value to be graphed is inside the brackets).[/COLOR]*

NagiosGrapher works to graph localhost ping, number of users and swap usage but not CPU load.

I checked ngraph.log and it shows this for my other hosts (the other hosts don't have any graphs working):

[COLOR="Red"]2009-12-07 13:26:33 PIPE: MyServerName1	CPU Load	CPU Load 1% (5 min average)	5 min avg Load=1%;80;90;0;100	1260156368
2009-12-07 13:26:33 REGEX: 3 blocks for 'CPU Load' found.
2009-12-07 13:26:33 REGEX: graph_value=15min
2009-12-07 13:26:33 REGEX: output=plugin.
2009-12-07 13:26:33 REGEX: regex=m/,(\d+[\.,]\d+)($|critical|warning)/i
2009-12-07 13:26:33 REGEX: perfdata=cpu load 1% (5 min average)
2009-12-07 13:26:33 REGEX: NO MATCH.
2009-12-07 13:26:33 VALUES: [MyServerName1][CPU Load]:No matching output values found...
2009-12-07 13:26:33 PIPE: [/COLOR]

Again I think it's my inability to use the regular expressions required for translating data to NagiosGrapher but I'm not sure what to do.I should also state I have check_load.ncfg (not disabled) yet no CPU load data is being graphed.

So in summary my 2 issues are:
1. Other hosts being monitored via nagios don't have graphs (apart from localhost)
2. CPU load and disk checks aren't being graphed.

THANKS for any help in advance.
Much appreciated,
Dom

---

