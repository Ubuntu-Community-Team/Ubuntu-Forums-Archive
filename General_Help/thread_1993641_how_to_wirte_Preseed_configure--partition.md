---
title: "how to wirte Preseed configure--partition"
date: 2012-06-02
forum: General Help
---

### Post by luofeiyu on 2012-06-02
i want to make automatic installation of Debian Squeeze,my partition are: sda1 / 20g 
sd2 /boot 200m 
sd3 / 15g 
how to write it in the preconfiguration of partition? 
d-i ????such as:

d-i partman-auto/choose_recipe select atomic

         300 4000 7000 ext3
	        $primary{ }
	        $bootable{ }
	        method{ format }
	        format{ }
	        use_filesystem{ }
	        filesystem{ ext3 }
	        mountpoint{ / } .
	
	64 512 300% linux-swap
	        method{ swap }
	        format{ } .
	
	100 10000 1000000000 ext3
	        method{ format }
	        format{ }
	        use_filesystem{ }
	        filesystem{ ext3 }
	        mountpoint{ /home } .

what is the meaning of :

1.300 4000 7000 ext3  ,300?4000?7000?
2.64 512 300%         ,64?512?300%?

---

