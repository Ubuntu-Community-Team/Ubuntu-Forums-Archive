---
title: "frustration with intel 9465 BGN wirless"
date: 2010-03-22
forum: General Help
---

### Post by younus_malik on 2010-03-22
tried with ubuntu 9.10 after all updates (wired connection) & ubuntu 10.4

i dont know what to do. waisted two days to connect to internet but in vail...

it shows the wireless connections and when choose one to connect, it keeps rotating the icon for a minute or two and then ask for the wep key again. i dont know whats going on... everytime i try to be a complete ubuntu convert, something goes terribly wrong :(

btw ubuntu 10.4 looks stunning & promising

---

### Post by bobcollard on 2010-03-22
> **younus_malik said:**
> tried with ubuntu 9.10 after all updates (wired connection) & ubuntu 10.4

i dont know what to do. waisted two days to connect to internet but in vail...

it shows the wireless connections and when choose one to connect, it keeps rotating the icon for a minute or two and then ask for the wep key again. i dont know whats going on... everytime i try to be a complete ubuntu convert, something goes terribly wrong :(

btw ubuntu 10.4 looks stunning & promising
It asks for 128bit passphrase or 40/128bit pass key depending on the choice bar.  Be sure you are putting it in the right place.  I use a 40bit pass key.

---

### Post by younus_malik on 2010-03-22
yeah i have got 40 bit and it works fine on windows 7 and xp.. it does not work with ubuntu 9.10 & 10.4 beta 1

---

### Post by ajgreeny on 2010-03-22
I think bobcollard is saying you should check whether you have entered the passphrase (the word you typed in when you set up the wireless) or the encrypted key.  Depending on which you choose in the wireless adapter setup you are attempting to deal with I think often you need the encrypted key entered, if I remember correctly, not the actual word you chose.

---

### Post by younus_malik on 2010-03-22
i did connect once or twice but then but for last last one day its not connecting anymore... especially when i installed ubuntu 9.10, my wireless works after one ore two tries, then after the update it never worked. similarly 10.4 never connected as of i remember.

so i do know that my key is right and it definitely working...

---

### Post by younus_malik on 2010-03-24
can someone please help?

---

### Post by kazakore on 2010-03-24
Dunno, my laptop using the same wireless card and I've been using it wirelessly with little difficulty since day one. (Note the little. Some serious niggles but it is working.)

You sure you know the difference between WEP(Hex), WEP(ASCII) and WPA 1&2?

I use WEP(ascii) at work, no problems. I use WPA2 Personal at home, although this does not remember my password and I have to enter it every single time.

I also have an issue that I have to restart my PC after every single change made in the Network Settings.

One of the most useful things to remember is to try "iwlist scan" into a terminal. If it fails to scan anything (can't remember the two messages I was getting) you are unlikely to get anything to happen without a restart, unless you are luckier than me.

The fact you say you have a list of networks to choose from is a good start and sounds like your adapter is being seen and is scanning available wireless networks though. More than I could get mine to do for a little while.


I did briefly install another network manager and that did solve the having to restart problem but it would only connect to the internet for a few bytes of downloads before hanging and having to wait ages to reconnect (although currently if something breaks my connection I usually have to restart too.) This is one of the things I've been meaning to get help on...

---

