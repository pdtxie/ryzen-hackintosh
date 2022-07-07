# ryzen-hackintosh

---
### specs:
- r7 5800x
- 6900xt (reference)
- 32gb ram
- 970 pro + 970 evo (macos uses 970 evo)
- asus x570i 
- BCM94350ZAE wifi card – i heavily recommend *against* this card, even though it's a supported airport card, it's *not-native* and has caused me more problems than it should have – spend a bit more money and buy a better one

**i am not responsible if you mess up your computer using any of my files**

**CHANGE THE SERIAL NUMBER AND ALL THAT STUFF**
___

# what works, what doesn't, and todo 

---
### what works
- bluetooth and wifi
- sleep
- ethernet
- adobe apps (apart from some instability)
- handoff
- universal clipboard
- imessage + text message forwarding
- EDIT: audio ~~(voodoohda not injecting in 11.4, using applealc - no mic)~~ voodoo is injected throgh /l/e so mic works, but audio definitely worse than applealc
- usb (usb mapped)
- EDIT: ~~restrict events~~ REMOVED - DON'T USE RESTRICT EVENTS IF YOU WANT SYSTEM UPDATES!
- continuity features (airdrop, continuity camera/sketch/markup)
- good amd cpu performance (enable Shaneee's fix pat kernel patch and disable algrey's one) (note: this might break nvidia gpu support or something)

---
### what doesn't work
- sidecar (no igpu)
- watch unlock - seems like watch unlock is a bit of a hit or miss with normal macs too so ¯\_(ツ)_/¯
- apple pay - no t2 chip will never work
- ~~look up / dictionary thing ?~~ ok fixed i copied the .dictionary files from my laptop 
- ~~perfect wake from sleep, but requires two keyboard taps, one to wake the system, and the second to wake the monitor, i think i might be able to fix this with an acpi device or something~~ tried to fix but doesn't seem fixable

---
### todo
- ~~fix slow opencore boot (10sec from post to opencore)~~ FIXED! DISABLE SATA IN BIOS AND NOW POST TO OPENCORE = <1sec
- ~~fix occasional freezes (although seems to be bs issue)~~ doesn't seem to be happening after i did something with swap
- manually make ssdts
- boot hangs at "ignoring kext cache invocation from early boot"\ -> bigsur issue though? - if you upgrade to monterey, this issue is fixed and boot time is about ~2 seconds from bios!

___

# files (ssdts+kexts)

---
### ssdts
- SSDT-EC-USBX-DESKTOP

---
### kexts
Wifi and Bluetooth:
- AirportBrcmFixup (remember to disable the 4360 injector, no longer in use 11+)
- BrcmBluetoothInjector (**for monterey use BlueToolFixup instead, remove this injector**)
- BrcmFirmwareData
- BrcmPatchRAM3

Ethernet:
- SmallTreeIntel82576 (**doesn't work in monterey**)

Lilu:
- Lilu
- ~~NVMeFix~~ (kernel panics with this on)
- VirtualSMC
- WhateverGreen
- SMCAMDProcessor

USB:
- USBMap (this is a usb map for the asus x570i ONLY, DO NOT USE FOR YOURS)

Other:
- AMDRyzenCPUPowerManagement
- AppleMCEReporterDisabler (i dont actually know what this does but apparently it prevents amd cpus from kernel panicking)







___

# other
___

### BIOS settings
- Above 4G Decoding ON
- SATA OFF
- XHCI Handoff OFF


### credits
- dortania and acidanthera: https://dortania.github.io, https://github.com/acidanthera

