---
title: "USB programming in Linux"
date: 2010-12-16
forum: General Help
---

### Post by mahesh123 on 2010-12-16
Hello every one
            I connect an USB mouse to port, where i have to read the raw  information from the device and use the same data for my own  application.
          i wrote the code using libusb library.After opening the device  successfully i tried to claim the interface. But its giving error while  claiming that device.When i write the detach kernal function only it  can able to claim the interface.

#ifdef LINUX
        libusb_detach_kernel_driver(devh, 0);
#endif

        r = libusb_set_configuration(devh, 1);
        if (r < 0) {
                fprintf(stderr, "libusb_set_configuration error %d\n", r);
                goto out;
        }
        printf("Successfully set usb configuration 1\n");
        r = libusb_claim_interface(devh, 0);
        if (r < 0) {
                fprintf(stderr, "libusb_claim_interface error %d\n", r);
                goto out;
        }
        printf("Successfully claimed interface\n");

        r = libusb_bulk_transfer(devh, ENDPOINT_INT_IN, buf,sizeof(buf), &transferred, TIMEOUT);
             
        if (r < 0) {
                fprintf(stderr, "Interrupt read error %d\n", r);
                return r;
        }

        for(i = 0;i < 5; i++) {
                if(i%8 == 0)
                        printf("\n");
                printf("%02x ",buf[i]);
           
        }

is this correct way to get the data from the mouse.
            
          please suggest me how to go through, and some suggestions  regarding this so that i can refer the same and get solved from this  problem, 
awaiting for your valuable information 

Thank you

---

