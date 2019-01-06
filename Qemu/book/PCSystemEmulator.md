
## 2. Qemu PC系统模拟器 ##

### 2.1 介绍 ###

Qemu PC 系统模拟器可以模拟如下的外围设备：

- i440FX 主机 PCI 桥和 PIIX3 PCI 链接 ISA 的桥
- Cirrus CLGD 5446 PCI VGA 视频卡，或者带有Bochs VESA扩展（硬件级别，包括所有非标准模式）的哑 VGA 视频卡
- PS/2 鼠标和键盘
- 2 PCI IDE 接口，可以支持硬盘和 CD-ROM
- 软盘
- PCI 和 ISA 网卡
- 串口
- IPMI BMC 外部或内部的，两者之一
- Creative SoundBlaster 16 声卡
- ENSONIQ AudioPCI ES1370 声卡
- Intel 82801AA AC97 Audio 兼容声卡
- Intel HD Audio Controller 和 HDA 解码器
- Adlib (OPL2) - Yamaha YM3812 兼容芯片
- Gravis Ultrasound GF1 声卡
- CS4231A 兼容声卡
- PCI UHCI, OHCI, EHCI or XHCI USB 控制器和虚拟的 USB-1.1 集线器

SMP 最多支持255个 CPU，Qemu 使用 PC BIOS 来自于 Seabios 项目和 Plex86/Bochs LGPL VGA BIOS。Qemu 使用 Tatsuyuki Satoh 的 YM3812 模拟。Qemu 使用 `Tibor "TS" Schütz` GUS 模拟（GUSEMU32 http://www.deinmeister.de/gusemu/）。

注意，默认情况下 GUS 与并行端口共享 IRQ（7），因此必须设置 Qemu 不使用并口，这样才能让 GUS 正常工作。可选方案是将 GUS 分配使用其他未使用的 IRQ。

```
qemu-system-i386 dos.img -soundhw gus -parallel none

// 可选方案
qemu-system-i386 dos.img -device gus,irq=5
```

CS4231 是Windows 音频系统使用的芯片，GUSMAX 的产品。

### 2.2 快速开始 ###

下载并且解压 Linux 系统镜像（linux.img），然后在命令行输入：

```
qemu-system-i386 linux.img
```

Linux 系统就会引导并且进入命令行显示输入命令提示符。




