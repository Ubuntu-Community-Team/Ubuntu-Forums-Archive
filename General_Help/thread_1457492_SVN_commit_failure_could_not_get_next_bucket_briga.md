---
title: "SVN commit failure: could not get next bucket brigade"
date: 2010-04-18
forum: General Help
---

### Post by jrop on 2010-04-18
So here's the problem: I have an SVN repo setup on my home server, and someone on the team cannot complete a commit operation.  The errors are given below.

Any help would be greatly appreciated!
[U][B]
Version Info[/B][/U]:
[INDENT]Apache: 2.2.12
SVN: 1.6.5
Ubuntu: 9.10 (Karmic)
[/INDENT]_**Error on the Server (from the logs)**_:

[LIST]
[*]129.82.230.210 - dalton [18/Apr/2010:14:45:34 -0600] "PUT /svn/dynamicsim/!svn/wrk/dadf5925-61b6-434f-8914-4f4a9bf40ecc/SimData.cpp HTTP/1.1" 204 141 "-" "SVN/1.6.9 (r901367) neon/0.29.0"
[*][Sun Apr 18 14:50:35 2010] [error] [client 129.82.230.210] Could not get next bucket brigade  [500, #0]
[/LIST]

_**Error for the client**_:
Sending        DynamicSim.cpp
Sending        SimData.cpp
Transmitting file data ..svn: Commit failed (details follow):
svn: Server sent unexpected return value (500 Internal Server Error) in
response to PUT request for
'*/svn/dynamicsim/*!svn/wrk/dadf5925-61b6-434f-8914-4f4a9bf40ecc/DynamicSim.cpp'

---

### Post by jrop on 2010-04-21
bump

---

