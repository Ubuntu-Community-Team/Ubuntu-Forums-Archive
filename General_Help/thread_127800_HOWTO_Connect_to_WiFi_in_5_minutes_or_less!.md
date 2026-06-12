---
title: "HOWTO: Connect to WiFi in 5 minutes or less!"
date: 2006-02-09
forum: General Help
---

### Post by Leiki on 2006-02-09
A couple of days ago, I created a thread asking for help on how to make my wireless card work. Ubuntu detected my card, and even displayed the signal strength, but I still could not get on the internet. Nothing worked, and those 2 days I spent as much time as I could to find out how to make it work.

I almost lost hope...when I found the way. I don't know where I found this, but I saved this in a text file so I could never lose it. ;) The person explaining it said it was for a certain wireless card I didn't have, but I tried it anyway and it worked. So I believe this works universally. All this is is typing a few commands in the terminal. Here's how:

1. Open your terminal. (Easy so far, yes?)

2. **sudo iwconfig ath0 channel 6**. (Or whatever channel your card is on, but 6 is the common one.)

3. **iwlist scan** - This gives you a MAC address that you will need later. Make sure you use the MAC address in cell 1.

4. **sudo iwconfig ath0 essid "NETWORK NAME"** - Replace NETWORK NAME with the ESSID (or name) of your network. Keep the quotes.

5. **sudo iwconfig ath0 ap XX:XX:XX:XX:XX:XX** - Replace the X's with the MAC address we found by doing iwlist scan.

6. **sudo iwconfig ath0 key XXXXXXXXXX** - Replace the X's with the WAP key you need in order to connect to it.

7. **sudo dhclient** - This is to check if it worked right. Uh...if it displays a lot of stuff with the words "listing on" and "sending on" over and over, it worked!

That's it! Of course, you are free to post any questions or comments on this.

The only problem I have is I have to do this everytime I startup Ubuntu. Anyway to to keep these settings?

---

### Post by Leiki on 2006-02-10
Hm...this is either a very well known thing or a very bad thing to do...

---

### Post by byen on 2006-02-10
I really like the part that you want to share this. Cool! But why not use a graphical application like NetworkManager or Wifi radar or the GTKWifi Project (listed in the 3rd party forum in this very site)? it only takes a few seconds using these and what more? its easy on the fingers too..!

---

### Post by Leiki on 2006-02-10
Byen, thanks for your input. That's a good point I forgot to mention. Since I'm still kind of new to Ubuntu, I had trouble installing things like wifi-radar and ndiswrapper. So this is my last resort, I guess. Maybe this should be renamed "Connect to WiFi in 5 minutes or less...for people with software installation disabilites!"

---

### Post by byen on 2006-02-10
Leiki, I think I Know what you mean. Sometimes the excitement of getting stuff to work is so huge that you cant wait to share..! And that is one of the main reasons why forums like these are a lifesaver. Well... too bad you cannot get the above mentioned applications to work.(.I suggest you digg in more..as it would save some time for you too!)
But in anycase....thanks for the commands...Ive already backed them up...Just incase I may need them someday.
RockON!

---

