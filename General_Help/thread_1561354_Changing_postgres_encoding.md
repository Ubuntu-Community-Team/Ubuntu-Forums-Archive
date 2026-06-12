---
title: "Changing postgres encoding"
date: 2010-08-26
forum: General Help
---

### Post by ColdFFF on 2010-08-26
First off, I'm not 100% sure this is the right place to find support, so apologies if its not.


I have recently inherited the roles of our old senior developer/sysadmin (unfortunately without the payrise for the time being :( ), and I'm trying to clear up the horrible mess he has left us in.

One of our major gripes at the moment is that our database is currently using the US-ASCII encoding, which is absolutely horrible. As a UK based company, we are having particular issues with the £ character, or any chinese characters, especially for things like storing our incoming emails etc.

What we would like to do is convert our database to UTF8. I am aware of how to change and reload the configs to switch to UTF8, however what I am asking is, how would I go about converting our existing data to UTF8 as well?

From what I understand, postgres has 2 sets of encoding - the server encoding and the client encoding. Currently both are set to US-ASCII. If I were to arrange some maintenance time, and change the client encoding to UTF8 and then take a dump of the database, would this convert the specifically US-ASCII characters into the appropriate UTF8 characters?

I have already had a play around with the pg_dump command, using the -E flag to attempt to take a UTF8 dump. Unfortunately, trying to restore this dump on a development machine with both client and server encodings set to UTF8 results in only a partial restore - tables that may store a £ character (for example, for our ticketing system) fail to restore.

I think the issue we are having is that the current US-ASCII encoding *somehow* has stored a combination of ASCII, UTF8 and ISO 8859-1 characters. A typical error message on the above restore attempts is something along the lines of:
```
0xA3 is not a valid UTF8 byte sequence
```
(For reference 0xA3 is the byte sequence for ISO 8859-1 £)

Any ideas on what my options are?

---

