---
title: "Question on Memory size"
date: 2010-10-22
forum: General Help
---

### Post by rnjn.sinha on 2010-10-22
Hi, 

I am using **64 bit** 10.10 and have recently upgraded my system to have 4 GB RAM. However, the memory reported by free is ~3.2 GB. Any hints on how can use the full 4 GB available. 

Following are some relevant details 

dmidecode reports the following 
```

Handle 0x1000, DMI type 16, 15 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 4 GB
        Error Information Handle: Not Provided
        Number Of Devices: 2

Handle 0x1100, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x1000
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 2048 MB
        Form Factor: DIMM
        Set: None
        Locator: DIMM_1
        Bank Locator: Not Specified
        Type: DDR
        Type Detail: Synchronous
        Speed: 533 MHz (1.9 ns)
        Manufacturer: 7F98000000000000
        Serial Number: 010E9223
        Asset Tag: Not Specified
        Part Number:                   

Handle 0x1101, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x1000
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 2048 MB
        Form Factor: DIMM
        Set: None
        Locator: DIMM_3
        Bank Locator: Not Specified
        Type: DDR
        Type Detail: Synchronous
        Speed: 533 MHz (1.9 ns)
        Manufacturer: FFFFFFFFFFFFFFFF
        Serial Number: FFFFFFFF
        Asset Tag: Not Specified
        Part Number:

```

Following is the output of lshw
```

    *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: 7F98000000000000
             physical id: 0
             serial: 010E9223
             slot: DIMM_1
             size: 2GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: FFFFFFFFFFFFFFFF
             physical id: 1
             serial: FFFFFFFF
             slot: DIMM_3
             size: 2GiB
             width: 64 bits
             clock: 533MHz (1.9ns)


```

free -m 
```

             total       used       free     shared    buffers     cached
Mem:          3261       3177         84          0        101        743
-/+ buffers/cache:       2332        928
Swap:         1945          7       1938

```

---

### Post by cascade9 on 2010-10-22
Get a PAE kernel, then it should see more of your RAM (though I doubt you will see the 'full' 4GB, there is always some RAM reserved for system use, etc).

---

### Post by 3Miro on 2010-10-22
PAE kernel is 32-bit only.

You are using ddr 533, which means somewhat old system. Some of the older BIOS had to be manually set to "remap" the memory. Check with your bios settings, BIOS manual and you may have to update the BIOS (which can be tricky).

---

### Post by cascade9 on 2010-10-22
Of course PAE is 32bit only....64bit doesnt have the 3.somethign GB RAM limit, so there wouldnt be much point making a PAE 64bit kernel LOL. 

It could be an older motherboard, or it could just be that the motherboard has defaulted to the lowest speed possible. I've seen more than a few motherboards that will do that.

---

### Post by SlugSlug on 2010-10-22
or onboard gfx supping up about half a gig ram??

---

