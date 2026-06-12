---
title: "Help, quick, someone, anyone! LAMP has gone crazical!"
date: 2009-08-26
forum: General Help
---

### Post by jasonwipos on 2009-08-26
I have written a script to automate posts to my blog but I had an error in the script. I forgot to empty $body on each iteration. I noticed when I stopped the script it was still running, still making posts. I tried stopping and starting apache, but it's STILL running. What am I going to do!!!

	$qry = "SELECT DISTINCT Resort, Destination FROM Hotels ORDER BY RAND()";
	$rset = mysql_query($qry);
	while($row =  mysql_fetch_array($rset)){
		$body .= "<a href=\"http://www.book2go.co.uk/deals/Self-Catering-".str_replace(" ","-",$row['Destination'])."-".str_replace(" ","-",$row['Resort']).".html\">".$phrase[rand(0,5)].$row['Resort']."</a>. ".$midphrase[rand(0,2)];
		$body .= "<a href=\"http://www.book2go.co.uk/deals/Bed-And-Breakfast-".str_replace(" ","-",$row['Destination'])."-".str_replace(" ","-",$row['Resort']).".html\">".$phrase[rand(0,5)].$row['Resort']."</a>. ".$midphrase[rand(0,2)];
		$body .= "<a href=\"http://www.book2go.co.uk/deals/Half-Board-".str_replace(" ","-",$row['Destination'])."-".str_replace(" ","-",$row['Resort']).".html\">".$phrase[rand(0,5)].$row['Resort']."</a>. ".$midphrase[rand(0,2)];
		$body .= "<a href=\"http://www.book2go.co.uk/deals/Full-Board-".str_replace(" ","-",$row['Destination'])."-".str_replace(" ","-",$row['Resort']).".html\">".$phrase[rand(0,5)].$row['Resort']."</a>. ".$midphrase[rand(0,2)];
		$body .= "<a href=\"http://www.book2go.co.uk/deals/All-Inclusive-".str_replace(" ","-",$row['Destination'])."-".str_replace(" ","-",$row['Resort']).".html\">".$phrase[rand(0,5)].$row['Resort']."</a>. ".$midphrase[rand(0,2)];
		wpPostXMLRPC("Holiday offers to ".$row['Destination'],$body,"http://news.book2go.co.uk/xmlrpc.php","admin","xxxxxx",array('Offer'));
		sleep(150);
	}

---

### Post by bmorency on 2009-08-26
is there any way to stop php or the db server?

---

### Post by dmonkey on 2009-08-26
Can't you just kill apache?

apachectl stop

EDIT: But wait, you said you tried that already. I can't see how the script can carry on running if apache is not. Try explicitly killing apache:

killall -15 apache

and, at worst

killall -9 apache

---

### Post by credobyte on 2009-08-26
Try:
```
sudo /etc/init.d/mysql stop

```

---

### Post by jasonwipos on 2009-09-14
Yeah I tried to use the terminal to kill it off like, but ubuntu being robust as it is, it just seemed to carry on from when I stopped it. I had to shut down everything and reboot.

Thanks guys.

---

