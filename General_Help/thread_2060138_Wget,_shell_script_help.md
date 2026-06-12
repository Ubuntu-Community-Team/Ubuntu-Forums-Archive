---
title: "Wget, shell script help"
date: 2012-09-19
forum: General Help
---

### Post by Green_Star on 2012-09-19
I am trying to download a url using wget, and parse the data from the downloaded html. So, first I simply tried to download the url(with some url parameters, ex: [www.abc.com/goodone.aspx?dateday=1&datemonth=2](www.abc.com/goodone.aspx?dateday=1&datemonth=2))

Problem1: Wget downloaded the file and still waiting for something. Wget wont return to shell prompt. 

Problem2: The html in downloaded one and the html in browser are not same. I mean some part is missing in downloaded version. I think that missing part supposed to generate using the variables I am passing in URL. 

how do I fix above two things? If I can fix these two, then I have to write some shell logics to parse data from html. 

thanks in advance.

---

### Post by Green_Star on 2012-09-19
Never mind, putting the double quotes around the url seems working.

---

