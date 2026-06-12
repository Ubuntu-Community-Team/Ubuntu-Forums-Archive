---
title: "#2002 Cannot log in to the MySQL server"
date: 2012-03-19
forum: General Help
---

### Post by JimTheSailor on 2012-03-19
The story:
A couple days ago I had created a new database and added a table to it using phpMyAdmin running on the Chrome browser. I then attempted to do something else, don't remember what, using the same software, when Chrome crashed.
I then could not get into the database using my name. (I had done everything else using my name.) I could however get in using root.
I could also log into MySQL using "mysql -h localhost -u root -p" 

I decided to stop and restart MySQL using "sudo stop mysql" and "sudo start mysql".
Since then I have not been able to get into MySQL at all.

Using phpMyAdmin I get "#2002 Cannot log in to the MySQL server"
Using "mysql -h localhost -u root -p" I get "ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)"
Using "sudo ls -l /var/run/" I see a list of directories and files including
drwxr-xr-x 2 mysql      root         40 2012-03-19 12:58 mysqld"
But if I use "sudo ls -l /var/run/mysqld" I see no files at all.
Thanks for any help you can give me.
Jim

---

### Post by Habitual on 2012-03-19
is mysqld running?

Terminal >
```
ps -e | grep mysql
```

---

### Post by JimTheSailor on 2012-03-19
"ps -e | grep mysql" displays nothing.

However, " sudo /etc/init.d/mysql restart" gives the following:
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart mysql
start: Job is already running: mysq

---

### Post by iiz on 2012-03-20
Try
```
sudo service mysqld start
```

or
```
sudo mysqld &
```

Better to use method #1

---

### Post by Todalozyzok on 2012-03-20
Êîìïàíèÿ Ãèäðî-ÃÀÐÀÍÒ çàíèìàåòñÿ ïðîèçâîäñòâîì ðåçèíî-òåõíè÷åñêèõ èçäåëèé. Â ñïåêòð èõ ïðîäóêöèè âõîäÿò: ãèäðîøïîíêè, [ ãåðíèòîâûé øíóð](http://www.gernit.ru)   , äåôîðìàöèîííûå  øâû, [áåíòîíèòîâûé øíóð](http://www.gidroshponka.ru/2011-02-06-21-02-13.html)  , øíóðû èç ãèäðîôèëüíîé ðåçèíû, [ áåíòîíèòîâûå ìàòû](http://xn----8sbbeobt9aeakc2cdg3lf.xn--p1ai)    , [ïðîôèëèðîâàííûå ìåìáðàíû](http://www.membrana.su)   . Ýòî ëèøü íåáîëüøîé ïåðå÷åíü èõ ïðîäóêöèè. Ãèäðîøïîíêè ÃèäðîÊîíòóð ñåãîäíÿ ÿâëÿþòñÿ ëèäåðîì ïî öåíå è êà÷åñòâó è ïîëüçóþòñÿ îãðîìíûì ñïðîñîì ñðåäè ñòðîèòåëüíûõ îðãàíèçàöèé. Ãåðíèòîâûå øíóðû âûñîêîãî êà÷åñòâà ðàçëè÷íûõ ïëîòíîñòåé øèðîêî èñïîëüçóåòñÿ äëÿ ãåðìåòèçàöèè ìåæïàíåëüíûõ øâîâ è äåôîðìàöèîííûõ øâîâ çäàíèÿ. [Áåíòîíèòîâûå ìàòû Ðîñáåíò](http://www.rosbent.ru)    ÿâëÿþòñÿ àíàëîãîì ìàòîâ [ Voltex](http://xn----8sbbeobt9aeakc2cdg3lf.xn--p1ai)  , ìíîãî ëåò ïðèìåíÿþòñÿ íà ðûíêå ðÔ, èñïîëüçîâàëèñü íà ñîòíÿõ çíà÷èìûõ îáúåòîâ Ðîññèè. Òàêæå êîìïàíèÿ Ãèäðî-ÃÀÐÀÍÒ âûïîëíÿåò çàêàçû ðåçèíîâûõ èçäåëèé è èçäåëèé èç ÏÂÕ ïî ÷åðòåæàì çàêàç÷èêà. Öåíû âñåãäà íèçêèå, áåç íàêðóòîê ïåðåïðîäàâöîâ

---

### Post by JimTheSailor on 2012-03-20
"sudo service mysqld start" gives me "unrecognized service"

---

### Post by JimTheSailor on 2012-03-20
"sudo service mysqld start" gives me "unrecognized service"

"sudo mysqld &" gives me "[1] 5360"

---

### Post by JimTheSailor on 2012-03-20
[Todalozyzok]("http://ubuntuforums.org/member.php?u=1577811") I could not read your reply. This is what I see:

[URL="http://ubuntuforums.org/member.php?u=1577811"]Îáóñòðîéñòâî
Êîìïàíèÿ Ãèäðî-ÃÀÐÀÍÒ çàíèìàåòñÿ ïðîèçâîäñòâîì ðåçèíî-òåõíè÷åñêèõ èçäåëèé. Â ñïåêòð èõ ïðîäóêöèè âõîäÿò: ãèäðîøïîíêè, ãåðíèòîâûé øíóð , äåôîðìàöèîííûå øâû, áåíòîíèòîâûé øíóð , øíóðû èç ãèäðîôèëüíîé ðåçèíû, áåíòîíèòîâûå ìàòû , ïðîôèëèðîâàííûå ìåìáðàíû . Ýòî ëèøü íåáîëüøîé ïåðå÷åíü èõ ïðîäóêöèè. Ãèäðîøïîíêè ÃèäðîÊîíòóð ñåãîäíÿ ÿâëÿþòñÿ ëèäåðîì ïî öåíå è êà÷åñòâó è ïîëüçóþòñÿ îãðîìíûì ñïðîñîì ñðåäè ñòðîèòåëüíûõ îðãàíèçàöèé. Ãåðíèòîâûå øíóðû âûñîêîãî êà÷åñòâà ðàçëè÷íûõ ïëîòíîñòåé øèðîêî èñïîëüçóåòñÿ äëÿ ãåðìåòèçàöèè ìåæïàíåëüíûõ øâîâ è äåôîðìàöèîííûõ øâîâ çäàíèÿ. Áåíòîíèòîâûå ìàòû Ðîñáåíò ÿâëÿþòñÿ àíàëîãîì ìàòîâ Voltex , ìíîãî ëåò ïðèìåíÿþòñÿ íà ðûíêå ðÔ, èñïîëüçîâàëèñü íà ñîòíÿõ çíà÷èìûõ îáúåòîâ Ðîññèè. Òàêæå êîìïàíèÿ Ãèäðî-ÃÀÐÀÍÒ âûïîëíÿåò çàêàçû ðåçèíîâûõ èçäåëèé è èçäåëèé èç ÏÂÕ ïî ÷åðòåæàì çàêàç÷èêà. Öåíû âñåãäà íèçêèå, áåç íàêðóòîê ïåðåïðîäàâöîâ
[/URL]
Jim

---

