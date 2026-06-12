---
title: "Yahoo games issue with 9.10"
date: 2009-11-17
forum: General Help
---

### Post by Breila on 2009-11-17
I've installed both sun java and flash but yahoo games is giving me the following error when I try to go to this address ( [http://games.yahoo.com/games/ante?room=yahoo_1091747460&prof_id=chat_pf_1](http://games.yahoo.com/games/ante?room=yahoo_1091747460&prof_id=chat_pf_1) ): 
   **This game cannot be played using your current settings. Please, try the following:**

   
[LIST]
[*]Check to make sure that java is enabled in your browser. ([learn more]("http://help.yahoo.com/help/us/games/games-09.html"))
[*]If you do not have java installed you may [download it here]("http://www.java.com/en/download").
[*]To learn more about java support for browsers, visit our [help pages]("http://help.yahoo.com/help/us/games/games-09.html").
[/LIST]

---

### Post by Purdue_Grad on 2009-12-02
I had the same problem with 9.10 64 bit. Turns out the version of Java I had was too new. Mine would load the list of tables to join, but never loaded the applet when I joined a table. Ran the command below and aptitude downgraded and it worked next try. Hope it helps.
 sudo aptitude install sun-java6-plugin

---

