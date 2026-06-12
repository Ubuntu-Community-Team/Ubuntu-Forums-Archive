---
title: "Edubuntu 11.10 LTSP Image Problem"
date: 2011-11-24
forum: General Help
---

### Post by zxxgpx on 2011-11-24
I have an edubuntu machine running an LTSP server that I just updated to 11.10. The update went fine except the LTSP image is having problems.

After the update I tried creating a new LTSP image using ltsp-build-client. It will download the image but at the very end it gives me a dependency error.

The command I use it this. "ltsp-build-client --fat-client --fat-client-desktop edubuntu-desktop --arch i386"

It will come back and say edubuntu-desktop depends on ubuntu-desktop.

Any ideas why it fails building a new image?

---

### Post by wdmcquinn on 2012-02-15
I was having the exact same issue. I finally found the solution below [here]("https://help.ubuntu.com/community/UbuntuLTSP/FatClients").

The fat client plugin blacklists some packages that  don't make sense to have in a fat client chroot. Unfortunately in  Oneiric xdiagnose depends on one of those packages, apport, so the fat  client plugin needs to be manually edited for ltsp-build-client to  complete successfully. 
Run the following command 
```
sudo gedit /usr/share/ltsp/plugins/ltsp-build-client/Ubuntu/030-fat-client
```and remove the word "apport" from line 43. Save, exit, and continue with the steps below. 

After this i rebuilt the client and it worked perfectly.

---

### Post by zxxgpx on 2012-03-22
> **wdmcquinn said:**
> I was having the exact same issue. I finally found the solution below [here]("https://help.ubuntu.com/community/UbuntuLTSP/FatClients").

The fat client plugin blacklists some packages that  don't make sense to have in a fat client chroot. Unfortunately in  Oneiric xdiagnose depends on one of those packages, apport, so the fat  client plugin needs to be manually edited for ltsp-build-client to  complete successfully. 
Run the following command 
```
sudo gedit /usr/share/ltsp/plugins/ltsp-build-client/Ubuntu/030-fat-client
```and remove the word "apport" from line 43. Save, exit, and continue with the steps below. 

After this i rebuilt the client and it worked perfectly.

That fixed my problem!

Thank you for the help.

---

### Post by DultAnnongony on 2012-03-22
How Can I Have ****** Online [***** sale 2mg](http://www.archive.org/details/XanaxSales-BuyXanaxInMontanaMissouri ) ****** Spokesman Cheap Alprazolam Mexico ****** In Men Without Ed ****** ******* 	Prozac Side Effects During Pregnancy [Cheap Soma No Script](http://www.archive.org/details/BuyCheapSomaCodFreeFedex ) Amoxicillin X26 Clavulanate Potassium Prozac U94 ****** Performance Sexual Pleasure 	***** Throat [tramadol buy in usa without prescription cod](http://www.archive.org/details/TramadolInformationAndPricesHowMuchIsTramadolWhereCanIBuyTramadol ) Tramadol Florida Food Tramadol For Dogs Dose Serotonin Reuptake Inhibitors Soma Drug High  Women Chat ******* ***** Withdrawal Weed [fioricet for cluster headaches](http://www.archive.org/details/BuyFioricetAmexMastercardVisaCheckBankCreditCardMoneyUsdEuro ) Alprazolam Cost Prescription No Prescription International Tramadol Amazon Tadalafil Prescription Pil Online  ***** For Adhd [Docs dont presribe Adipex](http://www.archive.org/details/PriceOfAdipexInTheUk ) Tramadol Patients ****** Off Label Tadalafil Long Term Side Effects ****** ****** *******  Maoi And Prozac St John's Wort [clonazepam use](http://www.archive.org/details/ClonazepamOverdoseLongTermEffects ) How Many Mag Of ***** Methotrexate Lab Results High Dose Methotrexate Reviews  ****** And Psa Foundation Carvedilol Sulfa Allergy Mono Hives From Amoxicillin

---

