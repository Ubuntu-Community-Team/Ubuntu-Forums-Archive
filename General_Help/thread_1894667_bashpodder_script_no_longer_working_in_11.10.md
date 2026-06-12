---
title: "bashpodder script no longer working in 11.10"
date: 2011-12-13
forum: General Help
---

### Post by NautiusMaximus on 2011-12-13
I had a [bashpodder script]("http://lincgeek.org/bashpodder/") nicely set up and downloading all my podcasts reliably in Ubuntu 11.04. For those who aren't familiar with bashpodder, it's a simple bash script that runs as a cron job to download the podcasts that I've told it I subscribe to.

At the weekend, I did a clean reinstall to Ubuntu 11.10. With exactly the same (I think!) bashpodder script set up, it no longer works. Rather than downloading podcasts, it downloads associated graphics files.

This puzzles me. Has anything changed in the way Ubuntu interprets bash scripts that could explain this, or could there be another explanation?

To save you the trouble of looking up how bashpodder works, here is the business end of the script:


```
# Read the bp.conf file and wget any url not already in the podcast.log file:
while read podcast
	do
	file=$(xsltproc parse_enclosure.xsl $podcast 2> /dev/null || wget -q $podcast -O - | tr '\r' '\n' | tr \' \" | sed -n 's/.*url="\([^"]*\)".*/\1/p')
	for url in $file
		do
		echo $url >> temp.log
		if ! grep "$url" podcast.log > /dev/null
			then
			wget -t 10 -U BashPodder -c -q -O $datadir/$(echo "$url" | awk -F'/' {'print $NF'} | awk -F'=' {'print $NF'} | awk -F'?' {'print $1'}) "$url"
			((NPODS++))
		fi
		done
	done < bp.conf

```

Any ideas?

Thanks
NM

---

### Post by lincfessenden on 2011-12-13
I might have a few :)
First, check to see if you have xsltproc, wget and sed installed (xsltproc was not installed by default on my Mint 12 (Ubuntu11.10) based machine.  Make sure you have the parse_enclosure.xsl file there too.
And if you get bored you can try my beta package for it at [http://lincgeek.org/bashpodder/downloads/](http://lincgeek.org/bashpodder/downloads/)

---

### Post by NautiusMaximus on 2011-12-13
Yes! That's exactly the problem: xsltproc wasn't installed. I think it was installed by default in Ubuntu 11.04, but obviously it isn't in 11.10. So I installed it, and now everything seems to work again.

Thank you so much!

---

