---
title: "uniq -u :  does not seem to remove duplicate lines"
date: 2009-08-15
forum: General Help
---

### Post by cbear on 2009-08-15
I am trying to comb through my local.cf file and remove all the duplicate blacklist_from entries. I ran

```
uniq -u local.cf output.cf
```

It did trim about 45 lines out of the file. But, there are still many many duplicate lines. I thought maybe they were different some how, but not visible to the eye...BUT, I ran:

```
sort output.cf | uniq -dc

```
this gave me a line count output for all the dups, and there are still many many...as you can see (below).

HELP


root@LINUX03:/home/backups# sort output.cf | uniq -dc
3
11 #
12 blacklist_from [email]1800FLOWERS@e.1800flowers.com[/email]
2 blacklist_from [email]acrane@amgacademy.com[/email]
2 blacklist_from [email]alejmagna@hotmail.com[/email]
10 blacklist_from [email]alerts@personals.yahoo.com[/email]
3 blacklist_from [email]Allen_Brothers@mail.vresp.com[/email]
8 blacklist_from [email]Borders@e.borders.com[/email]
2 blacklist_from [email]buy.com_offers@enews.buy.com[/email]
5 blacklist_from [email]capitalone@email.capitalone.com[/email]
2 blacklist_from [email]customerservice@duebrightlive.info[/email]
2 blacklist_from [email]customerservice@ehealthinsurance.com[/email]
2 blacklist_from [email]customerservice@mymorepayhomeonline.info[/email]
2 blacklist_from [email]customerservice@youreraseduelive.info[/email]
2 blacklist_from [email]directv@customerinfo.directv.com[/email]
3 blacklist_from [email]email@email.creditreport.com[/email]
8 blacklist_from [email]email@email.hotels.com[/email]
4 blacklist_from [email]etrade@email.etradefinancial.com[/email]
30 blacklist_from [email]group-digests@linkedin.com[/email]
4 blacklist_from [email]HHonors@h3.hilton.com[/email]
4 blacklist_from [email]info@aiueducationonline.com[/email]
4 blacklist_from [email]info@birdiebug.com[/email]
2 blacklist_from [email]info@promo-em.jetblue.com[/email]
2 blacklist_from [email]info@samstailor.com[/email]
2 blacklist_from [email]invite@naymz.com[/email]
6 blacklist_from [email]iprint@specials.iprint.com[/email]
12 blacklist_from [email]JobAlerts@CyberCoders.com[/email]
2 blacklist_from [email]lilly@sportsub.com[/email]
16 blacklist_from [email]listmaster@thegolfchannel.com[/email]
7 blacklist_from [email]mail@netapp.com[/email]
2 blacklist_from [email]mail@news.beachcamera.com[/email]
2 blacklist_from [email]microsoft@reply.digitalriver.com[/email]
2 blacklist_from [email]mike.moreno_at_mbofpleasanton.com@mmserver.com[/email]
2 blacklist_from [email]Mimosa_Systems@mail.vresp.com[/email]
6 blacklist_from [email]movies@news.fandango.com[/email]
2 blacklist_from [email]mwilkinson@serrahs.com[/email]
2 blacklist_from [email]nancyp@saintmatthew.org[/email]
2 blacklist_from [email]newsletter@reply.ticketmaster.com[/email]
2 blacklist_from [email]notifications@email.etradefinancial.com[/email]
6 blacklist_from [email]NutriSystem@news.nutrisystem.com[/email]
4 blacklist_from [email]paypal@email.paypal.com[/email]
2 blacklist_from [email]PGATOUR@pgatouremail.com[/email]
2 blacklist_from [email]PGATOUR@weic11.com[/email]
4 blacklist_from [email]radioshack@em.radioshack.com[/email]
2 blacklist_from [email]Rebecca_Salie@mail.vresp.com[/email]
4 blacklist_from [email]replies@oracle-mail.com[/email]
10 blacklist_from [email]reply@igmemail.com[/email]
2 blacklist_from [email]rexspelling@resumespider.com[/email]
28 blacklist_from [email]rushinahurry@rushlimbaugh.com[/email]
2 blacklist_from [email]sanjoseexecutives@gmail.com[/email]
2 blacklist_from [email]store-news@amazon.com[/email]
4 blacklist_from [email]Store-News@ShopAETV.p0.com[/email]
2 blacklist_from [email]support@myremoveliability.info[/email]
2 blacklist_from [email]TheHartford@weic11.com[/email]
4 blacklist_from [email]updates@linkedin.com[/email]
4 blacklist_from [email]update@stubhub-mail.com[/email]
2 blacklist_from [email]ups@upsemail.com[/email]
2 blacklist_from [email]vmwareteam@connect.vmware.com[/email]
2 blacklist_from [email]voyages@viator.messages1.com[/email]
2 blacklist_from [email]WebEx@weic11.com[/email]

---

### Post by DaithiF on 2009-08-15
Hi,
the file needs to be sorted for uniq -u to do its stuff, so
```
sort somefile | uniq -u > outfile
```

the clue is in the manpage
```
man uniq

```
where it says 
Discard  all but one of **successive** identical lines from INPUT (or stan&#8208;
       dard input), writing to OUTPUT (or standard output)

---

### Post by DaithiF on 2009-08-15
(and sort -u is a shorter way to do the same thing)

---

### Post by cbear on 2009-08-15
Thanks, that did work.  But, as I suspected, the "unique" lines are perhaps not exactly what I am looking for.  I want the first the first occurance of the lines - just not the duplicates.  This command using sort/uniq is ONLY giving me unique lines and totally eliminating ALL the dups.  For example, I have 4 lines the read "blacklist_from [email]email@paypal.com[/email]".  I want to keep one instance of this line and eliminate the other three as they are redundant.

---

### Post by cbear on 2009-08-15
fixed it...

```
sort -u local.cf > new.file
```

---

