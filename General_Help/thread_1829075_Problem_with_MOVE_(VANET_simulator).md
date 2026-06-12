---
title: "Problem with MOVE (VANET simulator)"
date: 2011-08-20
forum: General Help
---

### Post by hameerabbasi on 2011-08-20
I have read the page [he]("http://lens1.csie.ncku.edu.tw/wiki/doku.php?id=%E2%80%A7realistic_mobility_generator_for_vehicular_networks")[http://lens1.csie.ncku.edu.tw/MOVE/examples.zip](http://lens1.csie.ncku.edu.tw/MOVE/examples.zip)[re]("http://lens1.csie.ncku.edu.tw/wiki/doku.php?id=%E2%80%A7realistic_mobility_generator_for_vehicular_networks")  about the VANET Mobility Generator called MOVE. I do hope you can help  me with a problem I'm facing while generating the *.cnet.cfg files (the  "Create Map" option). I have followed the instructions to the word as  given [here]("http://lens1.csie.ncku.edu.tw/MOVE/Example%20for%20step-by-step.pdf"), except that I may have changed the order of nodes and edges. While generating the map file, I get the following output:
[INDENT]Loading configuration... 
Warning: Please note that 'xml-node-files' is deprecated.
 Use 'node-files' instead.
Warning: Please note that 'xml-edge-files' is deprecated.
 Use 'edge-files' instead.
Error: No option with the name 'type' exists.
Warning: Please note that 'lanenumber' is deprecated.
 Use 'default.lanenumber' instead.
Warning: Please note that 'speed' is deprecated.
 Use 'default.speed' instead.
Warning: Please note that 'priority' is deprecated.
 Use 'default.priority' instead.
Warning: Please note that 'remove-geometry' is deprecated.
 Use 'geometry.remove' instead.
Warning: Please note that 'remove-isolated' is deprecated.
 Use 'remove-edges.isolated' instead.
Error: Could not load configuration '/home/shahid/MOVE/ex_Map.netc.cfg'.
Quitting (on error).
[/INDENT]If  possible, direct me to a way to solve this problem. The exact same  problem occurs when I try the example files created [here]("http://lens1.csie.ncku.edu.tw/MOVE/examples.zip"), except that I  generate the configuration myself.

If it helps, I have Ubuntu Linux 11.04 installed, with Sun Java  1.6u026 configured, and I have added jdom.jar to the extension  libraries.

Yours truly,
[COLOR=#888888]Hameer Abbasi[/COLOR]

---

### Post by hameerabbasi on 2011-11-26
For anyone that may be still having this problem, MOVE is incompatible with SUMO version 0.13.0. You have to use SUMO version 0.12.3. Hope this helps,

Hameer

---

