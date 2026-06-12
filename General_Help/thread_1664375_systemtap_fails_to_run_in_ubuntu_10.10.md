---
title: "systemtap fails to run in ubuntu 10.10"
date: 2011-01-10
forum: General Help
---

### Post by icoming on 2011-01-10
Hello,

I tried to install systemtap and run on ubuntu 10.10, but failed with the following error. I have followed instructions at [http://sourceware.org/systemtap/wiki/SystemtapOnUbuntu](http://sourceware.org/systemtap/wiki/SystemtapOnUbuntu).
I wonder what else should I do? And what does the error mean? I ran iotime.stp on scientific linux 6, and there is no problem. 
The version of systemtap I installed is version 1.3/0.147.

Best,
Da

> 
zhengda@zhengda-desktop:~$ sudo stap -v iotime.stp test.txt 100
Pass 1: parsed user script and 72 library script(s) using 18984virt/12832res/1880shr kb, in 90usr/0sys/103real ms.
Pass 2: analyzed script: 24 probe(s), 12 function(s), 21 embed(s), 34 global(s) using 180356virt/30660res/2828shr kb, in 380usr/130sys/500real ms.
Pass 3: using cached /home/zhengda/.systemtap/cache/9e/stap_9ed36c05820a0481030e94d26da7e7e5_23975.c
Pass 4: using cached /home/zhengda/.systemtap/cache/9e/stap_9ed36c05820a0481030e94d26da7e7e5_23975.ko
Pass 5: starting run.
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.r._ZN6AsicNII18ucode_class_caymanE23NITilingModeLookupTableE: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.r._ZTV15WritebacksBlockIN11mmEngineUVD16WRITEBACKS_BLOCKEE: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.r._ZTV15WritebacksBlockIN17mmEngineR600_IDCT16WRITEBACKS_BLOCKEE: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.r._ZTV15WritebacksBlockIN17mmEngineRV630_AVP16WRITEBACKS_BLOCKEE: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.r._ZTV15WritebacksBlockIN19mmEngineR600_DRMDMA16WRITEBACKS_BLOCKEE: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.r._ZTVN4Asic40MultiMediaEngine_Emulate_IDCT_FreeTSNodeE: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN10CMMSurface18setSurfAllocationsERA4_K14CMM_ALLOCATION: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListI10CMMProcessE11insertFirstEPS0_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListI11CMMResourceE10insertLastEPS0_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListI14CMMDriver_COREE10insertLastEPS0_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListI14CMMLockSiblingE10insertLastEPS0_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListI16CBIOSSharedBlockE11insertFirstEPS0_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListI16CBIOSSharedBlockE6removeEPS0_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListI19CMMPoolSystemMemoryE10insertLastEPS0_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListI19CMMPoolSystemMemoryE11insertFirstEPS0_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListI19CMMPoolSystemMemoryE12insertBeforeEPS0_S2_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListI21CMMPoolAsicAccessibleE10insertLastEPS0_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListI21CMMPoolAsicAccessibleE11insertFirstEPS0_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListI21CMMPoolAsicAccessibleE12insertBeforeEPS0_S2_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListI7CMMLockE12insertBeforeEPS0_S2_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListI7CMMNodeE12insertBeforeEPS0_S2_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListI9CMMTsNodeE11insertAfterEPS0_S2_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListIN7CMMlistI10CMMProcessE12SafeIteratorEE10insertLastEPS3_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListIN7CMMlistI10CMMProcessE12SafeIteratorEE6removeEPS3_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListIN7CMMlistI10CMMSurfaceE12SafeIteratorEE10insertLastEPS3_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListIN7CMMlistI10CMMSurfaceE12SafeIteratorEE6removeEPS3_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListIN7CMMlistI10MapCounterE12SafeIteratorEE10insertLastEPS3_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListIN7CMMlistI10MapCounterE12SafeIteratorEE6removeEPS3_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListIN7CMMlistI11CMMResourceE12SafeIteratorEE10insertLastEPS3_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListIN7CMMlistI11CMMResourceE12SafeIteratorEE6removeEPS3_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListIN7CMMlistI14CMMLockSiblingE12SafeIteratorEE10insertLastEPS3_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListIN7CMMlistI14CMMLockSiblingE12SafeIteratorEE6removeEPS3_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListIN7CMMlistI16CBIOSSharedBlockE12SafeIteratorEE10insertLastEPS3_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListIN7CMMlistI16CBIOSSharedBlockE12SafeIteratorEE6removeEPS3_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListIN7CMMlistI7CMMLockE12SafeIteratorEE10insertLastEPS3_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListIN7CMMlistI7CMMLockE12SafeIteratorEE6removeEPS3_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListIN7CMMlistI7CMMNodeE12SafeIteratorEE10insertLastEPS3_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListIN7CMMlistI7CMMNodeE12SafeIteratorEE6removeEPS3_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListIN7CMMlistI8CMappingE12SafeIteratorEE10insertLastEPS3_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListIN7CMMlistI8CMappingE12SafeIteratorEE6removeEPS3_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListIN7CMMlistI8mmEngineE12SafeIteratorEE10insertLastEPS3_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListIN7CMMlistI8mmEngineE12SafeIteratorEE6removeEPS3_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListIN7CMMlistI9CMMClientE12SafeIteratorEE10insertLastEPS3_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListIN7CMMlistI9CMMClientE12SafeIteratorEE6removeEPS3_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListIN7CMMlistI9CMMTsNodeE12SafeIteratorEE10insertLastEPS3_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListIN7CMMlistI9CMMTsNodeE12SafeIteratorEE6removeEPS3_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListIN7CMMlistI9QS_CLIENTE12SafeIteratorEE10insertLastEPS3_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN11CMMBaseListIN7CMMlistI9QS_CLIENTE12SafeIteratorEE6removeEPS3_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI17mmEngineRV630_UVDE10insertNOPsERPjS2_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI17mmEngineRV630_UVDE10lastReadTSEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI17mmEngineRV630_UVDE11EndMMSubmitEPj: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI17mmEngineRV630_UVDE13BeginMMSubmitEPj: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI17mmEngineRV630_UVDE13StartHWAccessEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI17mmEngineRV630_UVDE14SwitchEngineHWEN8mmEngine15MM_ENGINE_STATEE: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI17mmEngineRV630_UVDE14insertSubmitIBERPjP12QS_MMIBUFFER: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI17mmEngineRV630_UVDE15insertTimestampERPj14_LARGE_INTEGER: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI17mmEngineRV630_UVDE20setRingBufferAddressEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI17mmEngineRV630_UVDE22ReinitMultimediaEngineEb: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI17mmEngineRV630_UVDE23enablePrivilegeRegCheckEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI17mmEngineRV630_UVDE4initEP18mmEnginesContainer: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI17mmEngineRV630_UVDE8readRptrEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI17mmEngineRV630_UVDE9setReadTSE14_LARGE_INTEGER: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI17mmEngineRV630_UVDE9writeWptrEj: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI18mmEngineRS780_UVD2E10insertNOPsERPjS2_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI18mmEngineRS780_UVD2E10lastReadTSEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI18mmEngineRS780_UVD2E11EndMMSubmitEPj: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI18mmEngineRS780_UVD2E13BeginMMSubmitEPj: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI18mmEngineRS780_UVD2E13StartHWAccessEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI18mmEngineRS780_UVD2E14SwitchEngineHWEN8mmEngine15MM_ENGINE_STATEE: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI18mmEngineRS780_UVD2E14insertSubmitIBERPjP12QS_MMIBUFFER: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI18mmEngineRS780_UVD2E15insertTimestampERPj14_LARGE_INTEGER: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI18mmEngineRS780_UVD2E20setRingBufferAddressEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI18mmEngineRS780_UVD2E22ReinitMultimediaEngineEb: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI18mmEngineRS780_UVD2E23enablePrivilegeRegCheckEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI18mmEngineRS780_UVD2E4initEP18mmEnginesContainer: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI18mmEngineRS780_UVD2E8readRptrEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI18mmEngineRS780_UVD2E9setReadTSE14_LARGE_INTEGER: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13BaseUVDEngineI18mmEngineRS780_UVD2E9writeWptrEj: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN13process_space23ProcessValidationObject5validEj: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15AsicCypressplusI17ucode_class_bartsE13loadMicrocodeEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15AsicCypressplusI17ucode_class_bartsE21initPM4FeatureVersionEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15AsicCypressplusI17ucode_class_bartsEC1EjjjPVjR18asic_configuration: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15AsicCypressplusI17ucode_class_bartsEC2EjjjPVjR18asic_configuration: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15AsicCypressplusI17ucode_class_kauaiE13loadMicrocodeEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15AsicCypressplusI17ucode_class_kauaiE21initPM4FeatureVersionEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15AsicCypressplusI17ucode_class_kauaiEC1EjjjPVjR18asic_configuration: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15AsicCypressplusI17ucode_class_kauaiEC2EjjjPVjR18asic_configuration: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15AsicCypressplusI17ucode_class_turksE13loadMicrocodeEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15AsicCypressplusI17ucode_class_turksE21initPM4FeatureVersionEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15AsicCypressplusI17ucode_class_turksEC1EjjjPVjR18asic_configuration: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15AsicCypressplusI17ucode_class_turksEC2EjjjPVjR18asic_configuration: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15AsicCypressplusI18ucode_class_caicosE13loadMicrocodeEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15AsicCypressplusI18ucode_class_caicosE21initPM4FeatureVersionEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15AsicCypressplusI18ucode_class_caicosEC1EjjjPVjR18asic_configuration: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15AsicCypressplusI18ucode_class_caicosEC2EjjjPVjR18asic_configuration: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15CMMSurface_CORE18setSurfAllocationsERA4_K14CMM_ALLOCATION: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15GpsAddressRange16SetPhysicalStartE15_ULARGE_INTEGER: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15WritebacksBlockIN11mmEngineUVD16WRITEBACKS_BLOCKEE8allocateEP4AsicRA11_9_CMM_HEAP: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15WritebacksBlockIN11mmEngineUVD16WRITEBACKS_BLOCKEED0Ev: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15WritebacksBlockIN11mmEngineUVD16WRITEBACKS_BLOCKEED1Ev: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15WritebacksBlockIN17mmEngineR600_IDCT16WRITEBACKS_BLOCKEE8allocateEP4AsicRA11_9_CMM_HEAP: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15WritebacksBlockIN17mmEngineR600_IDCT16WRITEBACKS_BLOCKEED0Ev: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15WritebacksBlockIN17mmEngineR600_IDCT16WRITEBACKS_BLOCKEED1Ev: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15WritebacksBlockIN17mmEngineRV630_AVP16WRITEBACKS_BLOCKEE8allocateEP4AsicRA11_9_CMM_HEAP: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15WritebacksBlockIN17mmEngineRV630_AVP16WRITEBACKS_BLOCKEED0Ev: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15WritebacksBlockIN17mmEngineRV630_AVP16WRITEBACKS_BLOCKEED1Ev: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15WritebacksBlockIN19mmEngineR600_DRMDMA16WRITEBACKS_BLOCKEE8allocateEP4AsicRA11_9_CMM_HEAP: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15WritebacksBlockIN19mmEngineR600_DRMDMA16WRITEBACKS_BLOCKEED0Ev: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN15WritebacksBlockIN19mmEngineR600_DRMDMA16WRITEBACKS_BLOCKEED1Ev: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPcieI13GART_PT_ENTRYE14GetSegmentBaseEb9_GPS_HEAP: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPcieI13GART_PT_ENTRYE18InitializeBaseUSWCEy: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPcieI13GART_PT_ENTRYE19GetSegmentBaseEntryEb9_GPS_HEAP: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPcieI13GART_PT_ENTRYE21InitializeBaseCaptureEy: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPcieI13GART_PT_ENTRYE21InitializeBasePeerMmrEy: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPcieI13GART_PT_ENTRYE23InitializeBaseCacheableEy: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPcieI13GART_PT_ENTRYE29InitializeBasePeerFrameBufferEy: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPcieI13GART_PT_ENTRYE32ReserveRangeForPrivateAllocationEy9_GPS_HEAP: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPcieI15GART_PPPT_ENTRYE14GetSegmentBaseEb9_GPS_HEAP: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPcieI15GART_PPPT_ENTRYE18InitializeBaseUSWCEy: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPcieI15GART_PPPT_ENTRYE19GetSegmentBaseEntryEb9_GPS_HEAP: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPcieI15GART_PPPT_ENTRYE21InitializeBaseCaptureEy: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPcieI15GART_PPPT_ENTRYE21InitializeBasePeerMmrEy: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPcieI15GART_PPPT_ENTRYE23InitializeBaseCacheableEy: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPcieI15GART_PPPT_ENTRYE29InitializeBasePeerFrameBufferEy: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPcieI15GART_PPPT_ENTRYE32ReserveRangeForPrivateAllocationEy9_GPS_HEAP: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPcieI19GART_PT_ENTRY_RS480E14GetSegmentBaseEb9_GPS_HEAP: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPcieI19GART_PT_ENTRY_RS480E18InitializeBaseUSWCEy: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPcieI19GART_PT_ENTRY_RS480E19GetSegmentBaseEntryEb9_GPS_HEAP: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPcieI19GART_PT_ENTRY_RS480E21InitializeBaseCaptureEy: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPcieI19GART_PT_ENTRY_RS480E21InitializeBasePeerMmrEy: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPcieI19GART_PT_ENTRY_RS480E23InitializeBaseCacheableEy: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPcieI19GART_PT_ENTRY_RS480E29InitializeBasePeerFrameBufferEy: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPcieI19GART_PT_ENTRY_RS480E32ReserveRangeForPrivateAllocationEy9_GPS_HEAP: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPcieI19GART_PT_ENTRY_RS480ED0Ev: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPcieI19GART_PT_ENTRY_RS480ED1Ev: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17PageTableGartPppt8map_peerEPvy15_ULARGE_INTEGER: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17mmEngineR600_IDCT9setReadTSE14_LARGE_INTEGER: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN17mmEngineRV630_AVP9setReadTSE14_LARGE_INTEGER: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN18PageTableGartRS4808map_peerEPvy15_ULARGE_INTEGER: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN19ExecutableUnitsR60013setLastReadTSER14_LARGE_INTEGER12_QS_CP_RING_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN19ExecutableUnitsR60013setLastReadTSEx12_QS_CP_RING_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN19ExecutableUnitsR6008PM4allocEjPPj12_QS_CP_RING_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN19ExecutableUnitsR6008PM4queueEPPj12_QS_CP_RING_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN19ExecutableUnitsR6009PM4submitEPPjb12_QS_CP_RING_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN19mmEngineR600_DRMDMA20getTimestampsAddressEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN19mmEngineR600_DRMDMA9setReadTSE14_LARGE_INTEGER: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN21GpsMappedAddressRange16SetPhysicalStartE15_ULARGE_INTEGER: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN25CMMHeap_FRAME_BUFFER_COREI18CMMHeap_ASIC_LOCALE10expandHeapEy: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN25CMMHeap_FRAME_BUFFER_COREI18CMMHeap_ASIC_LOCALE10shrinkHeapEb: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN30CMMHeap_ASIC_ACCESSIBLE_MEMORY8pushPoolEP7CMMPool: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN30CMMHeap_FRAME_BUFFER_INVISIBLE10expandHeapEy: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN30CMMHeap_FRAME_BUFFER_INVISIBLE10shrinkHeapEb: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN4Asic19cacheTilingModeInfoER16MSF_SURF_ATTRIBS: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN4Asic19initAddressLibEntryEP26_CMM_SET_ADDRESSLIB_ENTRY_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN4Asic20initCopySurfaceEntryEP24_CMM_SET_CALLBACKS_ENTRY: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN4Asic28CMMTilingMode2AddrTilingModeE16_CMM_TILING_MODE: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN4Asic36invalidSourceCachesBefore3DRenderingEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN4Asic40MultiMediaEngine_Emulate_IDCT_FreeTSNodeD0Ev: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN4Asic40MultiMediaEngine_Emulate_IDCT_FreeTSNodeD1Ev: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN6AsicNII18ucode_class_caymanE13loadMicrocodeEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN6AsicNII18ucode_class_caymanE21initPM4FeatureVersionEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN6AsicNII18ucode_class_caymanE21initializeMicroEngineEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN6AsicNII18ucode_class_caymanE23initializeApertureStateEPN4Asic14APERTURE_STATEEP18SURFACE_PROPERTIES: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN6AsicNII18ucode_class_caymanE28CMMTilingMode2AddrTilingModeE16_CMM_TILING_MODE: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN6AsicNII18ucode_class_caymanEC1EjjjPVjR18asic_configuration: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN6AsicNII18ucode_class_caymanEC2EjjjPVjR18asic_configuration: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN7CMMHeap15createPoolSpaceI19CMMPoolSystemMemoryEEbj: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN7CMMHeap15createPoolSpaceI21CMMPoolAsicAccessibleEEbj: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN8AsicR60019initAddressLibEntryEP26_CMM_SET_ADDRESSLIB_ENTRY_: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN8AsicR60023EventWriteEopPacketInitEP21Type3_EVENT_WRITE_EOP: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN8mmEngine10submitMVPUI12_QS_POINTER_EEjjP9QS_CLIENTjT_jR14_LARGE_INTEGER: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN8mmEngine10submitMVPUIP12QS_MMIBUFFEREEjjP9QS_CLIENTjT_jR14_LARGE_INTEGER: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN9AsicRV63034program_HDP_SURFACEx_VIEW_registerEjPN8AsicR60014APERTURE_STATEE: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZN9AsicRV77034program_HDP_SURFACEx_VIEW_registerEjPN8AsicR60014APERTURE_STATEE: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZNK11R800AddrLib16HwlPreAdjustBankEjjP14_ADDR_TILEINFO: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZNK17PageTableGartPcieI13GART_PT_ENTRYE21GetSizePageTableEntryEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZNK17PageTableGartPcieI15GART_PPPT_ENTRYE21GetSizePageTableEntryEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZNK17PageTableGartPcieI19GART_PT_ENTRY_RS480E21GetSizePageTableEntryEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZNK25CMMHeap_FRAME_BUFFER_COREI18CMMHeap_ASIC_LOCALE16reportedCapacityEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZNK25CMMHeap_FRAME_BUFFER_COREI18CMMHeap_ASIC_LOCALE17reportedTotalFreeEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZNK25CMMHeap_FRAME_BUFFER_COREI18CMMHeap_ASIC_LOCALE20PrivateAreaTotalFreeEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZNK25CMMHeap_FRAME_BUFFER_COREI18CMMHeap_ASIC_LOCALE20get_addr_restrictionER16MSF_SURF_ATTRIBSP21MEMHEAP_ADDR_RESTRICT: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZNK4Asic37LowestPriorityHDPSurfaceApertureIndexEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZNK4Asic38HighestPriorityHDPSurfaceApertureIndexEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZNK7AddrLib15HwlSetupTileCfgEiP14_ADDR_TILEINFOP13_AddrTileModeP13_AddrTileType: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZNK8AsicR60037LowestPriorityHDPSurfaceApertureIndexEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZNK8AsicR60038HighestPriorityHDPSurfaceApertureIndexEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZThn32_N7GartAgp14AllocateMemoryER13GpsAllocation: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZThn408_N11GartCypress15CreatePageTableEP9GpsConfig: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZThn408_N13GartPpptRS60015CreatePageTableEP9GpsConfig: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZThn408_N13GartPpptRS60023InitializeGartRegistersEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZThn408_N13GartVmptRS78015CreatePageTableEP9GpsConfig: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZThn408_N13GartVmptRS78023InitializeGartRegistersEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZThn408_N13GartVmptRv77015CreatePageTableEP9GpsConfig: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZThn408_N13GartVmptRv77023InitializeGartRegistersEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZThn408_N19GartVmptRialtoRV6XX14CreateApertureEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZThn408_N19GartVmptRialtoRV7XX14CreateApertureEv: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZThn408_N7GartPci11UnmapMemoryE9_GPS_HEAPyy15_ULARGE_INTEGERb: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZThn408_N7GartPci14AllocateMemoryER13GpsAllocation: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZThn408_N7GartPci17AdjustMappingBaseE13GpsAllocation: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZThn408_N8GartPcie11UnmapMemoryE9_GPS_HEAPyy15_ULARGE_INTEGERb: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZThn408_N8GartPcie14AllocateMemoryER13GpsAllocation: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZThn408_N8GartPcie15CreatePageTableEP9GpsConfig: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZThn408_N8GartPcie17AdjustMappingBaseE13GpsAllocation: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZThn408_N8GartVmpt15CreatePageTableEP9GpsConfig: No such file or directory
staprun:send_a_relocation:331: ERROR: reloc name too long: .gnu.linkonce.t._ZThn408_N9GartRS48015CreatePageTableEP9GpsConfig: No such file or directory
^CWARNING: Number of errors: 0, skipped probes: 36
num_copy=0x0
copy_time=0x0
Pass 5: run completed in 0usr/40sys/5155real ms.
Pass 5: run failed.  Try again with another '--vp 00001' option.

---

