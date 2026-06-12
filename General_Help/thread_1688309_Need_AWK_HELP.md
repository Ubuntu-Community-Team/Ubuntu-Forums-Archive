---
title: "Need AWK HELP"
date: 2011-02-15
forum: General Help
---

### Post by bmj5242 on 2011-02-15
**[FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana][B]Need Development Help**[/FONT][/COLOR][/COLOR][/SIZE][/FONT][/B][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana] [/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[CENTER][CENTER][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana][/FONT][/COLOR][/COLOR][/SIZE][/FONT][/CENTER][/CENTER]
[FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]I need development help with a AWK Program.

1
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]2[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]3 THIS IS THE INPUT FILE – EACH EMPLOYEE MAY HAVE FROM 1 TO 30 RECORDS[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]4[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]5 1-4 Project[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]6 5-12 Employee[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]7 13-14 Sequence (MAYBE FROM 1 TO 30)[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]8 15-21 Work Code[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]9 22-22 Pri Code[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]10[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]11 9991|80100001|1|0389999|1|[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]12 9991|80100001|2|7070007|2|[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]13 9991|80100001|3|4912100|1|[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]14 9991|80100001|4|5990000|2|[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]15 9991|80100001|5|2500200|1|[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]16 9991|80100001|6|41401|2|[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]17 9991|80100001|7|515|1|[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]18 9991|80100001|8|4019|2|[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]19 9991|80100001|9|56210|1|[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]20[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]21 THIS IS THE OUTPUT (OPTION ONE)[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]22 ( NEED ONE CONTIGUOUS RECORD PER EMPLOYEE )[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]23[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]24 1586|80100001|0389999|7070007|4912100|599000|25002 00|41401|515|4019|56210|1|2|1|2|1|2|1|2|1|[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]25[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]26[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]27 THIS IS THE OUTPUT (OPTION TWO)[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana]
[/FONT][/COLOR][/COLOR][/SIZE][/FONT][COLOR=black][COLOR=black]28 ( NEED ONE CONTIGUOUS RECORD PER EMPLOYEE WITH OUTPUT CONTAINING ROOM FOR 30 WORK CODES AND 30 PRI CODES )
29
30 1586|80100001|0389999|7070007|4912100|599000|25002 00|41401|515|4019|56210||||||||||||||||||||||1|2|1 |2|1|2|1|2|1||||||||||||||||||||||
31
thank for the help.[/COLOR][/COLOR][FONT=Verdana][SIZE=1][COLOR=black][COLOR=black][FONT=Verdana][/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=Arial] [/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=Arial] [/FONT][/SIZE][/FONT]

---

### Post by aromo on 2011-02-15
First thing you need to do is code employees from 01 to 30 (two digits).  If you have employees with one digit code, it's going to screw any logic.

---

