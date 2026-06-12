---
title: "TTY-X switching time"
date: 2012-03-02
forum: General Help
---

### Post by samvkampen on 2012-03-02
This is probably not the fault of Ubuntu, and I don't know of what it might be, but whenever I switch between VT's and X (X->VT, VT->X and VT->VT) it takes a while (+-2seconds) to switch, and I find this very annoying when I am working both in the VT and on X.

I wondered, is there any way in which you can change the switch time/make it shorter?
Or is this my monitor's fault? Or the drivers?

-- Sam

---

### Post by Khayyam on 2012-03-02
> **samvkampen said:**
> [...] whenever I switch between VT's and X [...] it takes a while (+-2seconds) to switch

"+-2seconds" == plus minus two? That would be time travel via VT ... heh.

> **samvkampen said:**
> I wondered, is there any way in which you can change the switch time/make it shorter?Or is this my monitor's fault? Or the drivers?

The VT has to be re-drawn, and whatever is controling the display relinquish that control, so this can take .. ummm .. {mirco}seconds, but faster cards, and quality of the driver, will be a factor.

HTH ... khay

---

