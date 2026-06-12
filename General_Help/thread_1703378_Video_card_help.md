---
title: "Video card help"
date: 2011-03-09
forum: General Help
---

### Post by schwabdale on 2011-03-09
Hello,
I have a Dell Dimension E521. Its running Ubuntu 10.10. I would like to hook this up to a 
42 inch LCD Tv via HDMI. 

Can someone please recommend a video card with HDMI that would work good for this. 

I heard Nvidia was the way to go. Is this true?

Thanks in advance

---

### Post by grahammechanical on 2011-03-09
The general opinion is that Nvidia have been more helpful than ATI in producing drivers to get their cards working under Linux.

The standard or built in driver, if you want to think of it that way, works with most cards but is not able to use all the features that some cards are built for. This is why in Ubuntu we install drivers from Nvidia.

I am using at the moment a Nvidia GForce GT220 with the recommended Nvidia driver 260.19.06. It works fine.

The two things I suggest that you look out for are:

1) That the card has a HDMI connector. You do not want to connect to this monitor by VGA even if it does have a VGA connector. The thing will work but you will not get the benefit of HDMI to HDMI connection.

2) You avoid an Nvidia card that uses Optimus technology. At present Linux and hence, Ubuntu does not run the Optimus part very well. This needs development by Nvidia. I think that this is mainly a problem for those buying laptops. The card will work but the power saving capabilities of Optimus are not functional in Linux at present.

Regards.

---

### Post by schwabdale on 2011-03-09
If I buy the Nvidia GForce GT220, will it work right out of the box or will I have to install the driver?

---

