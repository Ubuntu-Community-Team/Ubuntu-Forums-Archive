---
title: "London Buses!!"
date: 2010-06-15
forum: General Help
---

### Post by mohammed85 on 2010-06-15
Hi guys,

I want to ask if any of you have been to London and been on one of its Buses, he would notice how quick was the transaction when he toucheed in his Oyster card.

I am wandering where is the database is stored and why it is so quick? I assume there is no connection established for every single transaction because the operation is so quick but at the same time how the controller has my latest travel journey details?

I am just looking for an overall design of the system?

I have heard it uses open-source!

---

### Post by Chesamo on 2010-06-15
Probably just a radio-based database system. The system only has to send and receive a few bytes; it's not that complicated. It's just like ATMs.

---

### Post by mohammed85 on 2010-06-15
thanks but where is the database?

---

### Post by cascade9 on 2010-06-15
AFAIK, the card itself holds only the balance and trip details (and probably only a limited number of trip details, but how many that is I have no idea). 

When you touch on, the card is updated with the difference in balance and the newest trip details, and later in the day (probably when the bus returns to the depot) the bus updates the central database in one big batch. 

We have the same system here, called a 'go card' (brisbane, australia). I wouldnt use it but our lovely governement decided to jack the prices for non 'go card' trips by about 30%, and removed the option to get weeky/monthy/6 monthy/yearly tickets (which were cheaper again than buying on the bus/train/ferry). Then they declare how much of a 'sucess' it is when the price jacking makes a huge number of people move from paper tickets to go cards. 

I'm disgused at the whole thing ](*,):x

---

### Post by Chesamo on 2010-06-15
> **mohammed85 said:**
> thanks but where is the database?
Probably on some server somewhere. Why?

---

