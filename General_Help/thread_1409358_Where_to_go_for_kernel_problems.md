---
title: "Where to go for kernel problems?"
date: 2010-02-17
forum: General Help
---

### Post by Xbehave on 2010-02-17
Basically 2.6.33-rc8 does not boot on my computer, unfortunately this seams far to specific to get help in the ubuntu help forums, so where do you go when you run into problems with your kernel?

Or does everybody else stick to distro related kernels/is too good to need help?

Also is there a better way to diff configs then just diff config-1 config-2, as sometimes disabling a section creates a lot of changes in the .config file when it is just one changed settings and the default diff syntax is a bit ugly compared to wikipedia diffs (any tips for diff options?)

```
3,4c3,4                                                                                                                                                           
< # Linux kernel version: 2.6.33-rc6                                                                                                                              
< # Tue Feb  2 22:51:25 2010                                                                                                                                      
---                                                                                                                                                               
> # Linux kernel version: 2.6.33-rc8                                                                                                                              
> # Mon Feb 15 23:58:29 2010                                                                                                                                      
556a557                                                                                                                                                           
> CONFIG_WIRELESS_EXT=y                                                                                                                                           
558a560,561                                                                                                                                                       
> CONFIG_WEXT_SPY=y                                                                                                                                               
> CONFIG_WEXT_PRIV=y                                                                                                                                              
568a572,574                                                                                                                                                       
> CONFIG_LIB80211_CRYPT_WEP=m                                                                                                                                     
> CONFIG_LIB80211_CRYPT_CCMP=m                                                                                                                                    
> CONFIG_LIB80211_CRYPT_TKIP=m                                                                                                                                    
631c637                                                                                                                                                           
< # CONFIG_VIRTIO_BLK is not set                                                                                                                                  
---                                                                                                                                                               
> CONFIG_VIRTIO_BLK=m                                                                                                                                             
633,655c639                                                                                                                                                       
< CONFIG_MISC_DEVICES=y                                                                                                                                           
< # CONFIG_AD525X_DPOT is not set                                                                                                                                 
< # CONFIG_IBM_ASM is not set                                                                                                                                     
< # CONFIG_PHANTOM is not set                                                                                                                                     
< # CONFIG_SGI_IOC4 is not set                                                                                                                                    
< # CONFIG_TIFM_CORE is not set                                                                                                                                   
< # CONFIG_ICS932S401 is not set                                                                                                                                  
< # CONFIG_ENCLOSURE_SERVICES is not set                                                                                                                          
< # CONFIG_CS5535_MFGPT is not set                                                                                                                                
< # CONFIG_HP_ILO is not set                                                                                                                                      
< # CONFIG_ISL29003 is not set                                                                                                                                    
< # CONFIG_DS1682 is not set                                                                                                                                      
< # CONFIG_C2PORT is not set                                                                                                                                      
<                                                                                                                                                                 
< #                                                                                                                                                               
< # EEPROM support                                                                                                                                                
< #                                                                                                                                                               
< # CONFIG_EEPROM_AT24 is not set                                                                                                                                 
< # CONFIG_EEPROM_LEGACY is not set                                                                                                                               
< # CONFIG_EEPROM_MAX6875 is not set                                                                                                                              
< # CONFIG_EEPROM_93CX6 is not set                                                                                                                                
< # CONFIG_CB710_CORE is not set                                                                                                                                  
< # CONFIG_IWMC3200TOP is not set                                                                                                                                 
---                                                                                                                                                               
> # CONFIG_MISC_DEVICES is not set                                                                                                                                
851,874c835                                                                                                                                                       
< CONFIG_NETDEV_1000=y                                                                                                                                            
< # CONFIG_ACENIC is not set                                                                                                                                      
< # CONFIG_DL2K is not set                                                                                                                                        
< # CONFIG_E1000 is not set                                                                                                                                       
< # CONFIG_E1000E is not set                                                                                                                                      
< # CONFIG_IP1000 is not set                                                                                                                                      
< # CONFIG_IGB is not set                                                                                                                                         
< # CONFIG_IGBVF is not set                                                                                                                                       
< # CONFIG_NS83820 is not set                                                                                                                                     
< # CONFIG_HAMACHI is not set                                                                                                                                     
< # CONFIG_YELLOWFIN is not set                                                                                                                                   
< # CONFIG_R8169 is not set                                                                                                                                       
< # CONFIG_SIS190 is not set                                                                                                                                      
< # CONFIG_SKGE is not set                                                                                                                                        
< # CONFIG_SKY2 is not set                                                                                                                                        
< # CONFIG_VIA_VELOCITY is not set                                                                                                                                
< # CONFIG_TIGON3 is not set                                                                                                                                      
< CONFIG_BNX2=m                                                                                                                                                   
< CONFIG_CNIC=m                                                                                                                                                   
< # CONFIG_QLA3XXX is not set                                                                                                                                     
< # CONFIG_ATL1 is not set                                                                                                                                        
< # CONFIG_ATL1E is not set                                                                                                                                       
< # CONFIG_ATL1C is not set                                                                                                                                       
< # CONFIG_JME is not set                                                                                                                                         
---                                                                                                                                                               
> # CONFIG_NETDEV_1000 is not set                                                                                                                                 
900c861,868                                                                                                                                                       
< # CONFIG_IPW2200 is not set                                                                                                                                     
---                                                                                                                                                               
> CONFIG_IPW2200=m                                                                                                                                                
> CONFIG_IPW2200_MONITOR=y                                                                                                                                        
> CONFIG_IPW2200_RADIOTAP=y                                                                                                                                       
> CONFIG_IPW2200_PROMISCUOUS=y                                                                                                                                    
> # CONFIG_IPW2200_QOS is not set                                                                                                                                 
> # CONFIG_IPW2200_DEBUG is not set                                                                                                                               
> CONFIG_LIBIPW=m                                                                                                                                                 
> # CONFIG_LIBIPW_DEBUG is not set                                                                                                                                
951c919                                                                                                                                                           
< # CONFIG_VIRTIO_NET is not set                                                                                                                                  
---                                                                                                                                                               
> CONFIG_VIRTIO_NET=m                                                                                                                                             
1395,1399c1363                                                                                                                                                    
< CONFIG_AGP=y                                                                                                                                                    
< CONFIG_AGP_AMD64=y                                                                                                                                              
< # CONFIG_AGP_INTEL is not set                                                                                                                                   
< # CONFIG_AGP_SIS is not set                                                                                                                                     
< # CONFIG_AGP_VIA is not set                                                                                                                                     
---                                                                                                                                                               
> # CONFIG_AGP is not set                                                                                                                                         
1406a1371                                                                                                                                                         
> # CONFIG_DRM_RADEON_KMS is not set                                                                                                                              
1408d1372                                                                                                                                                         
< # CONFIG_DRM_SIS is not set                                                                                                                                     
1980,1987c1944                                                                                                                                                    
< CONFIG_UIO=m                                                                                                                                                    
< # CONFIG_UIO_CIF is not set                                                                                                                                     
< # CONFIG_UIO_PDRV is not set                                                                                                                                    
< # CONFIG_UIO_PDRV_GENIRQ is not set                                                                                                                             
< # CONFIG_UIO_SMX is not set
< # CONFIG_UIO_AEC is not set
< # CONFIG_UIO_SERCOS3 is not set
< # CONFIG_UIO_PCI_GENERIC is not set
---
> # CONFIG_UIO is not set
2256c2213
< CONFIG_CRYPTO_GF128MUL=m
---
> # CONFIG_CRYPTO_GF128MUL is not set
2294c2251
< CONFIG_CRYPTO_MD4=m
---
> # CONFIG_CRYPTO_MD4 is not set
2304,2305c2261,2262
< CONFIG_CRYPTO_TGR192=m
< CONFIG_CRYPTO_WP512=m
---
> # CONFIG_CRYPTO_TGR192 is not set
> # CONFIG_CRYPTO_WP512 is not set
2320c2277
< CONFIG_CRYPTO_DES=m
---
> # CONFIG_CRYPTO_DES is not set

```

---

### Post by cariboo on 2010-02-17
Have a look at the Linux kernel mailing list [faq]("http://www.kernel.org/pub/linux/docs/lkml/"). It should tell you where to go for help.

Moved to General Help.

---

