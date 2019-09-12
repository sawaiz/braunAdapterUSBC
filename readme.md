# Braun USB-C Power Adapter
A charger adapter to provide a USB-C interface to some of the following products

- Braun
- Oral-B

Or any other simple 12V charger that consumes less than 500mA. Check your charger or device manual for compatiblity.

![renderIso1]

## Design
The stock charger provided with my Oral-B Genius 9000 travel case is rated at 12V and 400mA. The design will be set to match the voltage and exceed the current requirements so it works with as many similar porducts as possible. 

Using the USB 5V avalibilty as more adapter suppourt rather than the 15V and boosting the voltage to 12V from the 5V@3A would provide 800mA with perfect efficency letting us rate our charger safely at 500mA. The 12V profile is also being completely avoided since the 12V profile only existed in the REV 1.0 of the power delivery protocol and is not compatible with current standards. Using the 5V profile also allows us to not need a negotiator and instead just use two passive 5.1K resistors on the CC lines.

![renderIso2]

### Boost Converter
The Microchip [MIC2290](http://ww1.microchip.com/downloads/en/DeviceDoc/MIC2290-075A-Switch-PWM-Boost-Regulator-with-Internal-Schottky-Diode-and-Undervoltage-Lockout-DS20006038A.pdf) is a easy to implement boost converter with a intergrated switch and didoe requiring only external passives. A 10uH inductor, some input and output capacitors and resistors to set the output voltage are all that are needed. The 43.2K and 5k resistors are from the example in the datasheet to set the voltage to 12V.

![schematic]

## BOM
The bill of materials is availible in [`bom.csv`](bom.csv) and is copied into a table below.

| Ref Des | Qty | Manufacturer | MPN              | Description                       |
| ------  | --- | ------------ | ---------------- | --------------------------------- |
| C1 C2   | 2   | Samsung      | CL21A106KOQNNNG  | CAP CER 10UF 16V X5R 0805         |
| J1      | 1   | Amphenol ICC | 12401610E4#2A    | CONN RCP USB3.1 TYPEC 24P SMD RA  |
| L1      | 1   | Taiyo Yuden  | NRS5030T100MMGJ  | FIXED IND 10UH 1.7A 70 MOHM SMD   |
| R1 R2   | 2   | Yageo        | RC0402JR-075K1L  | RES SMD 5.1K OHM 5% 1/16W 0402    |
| R3      | 1   | Yageo        | RC0402FR-0743K2L | RES SMD 43.2K OHM 1% 1/16W 0402   |
| R4      | 1   | Yageo        | RC0402FR-074K99L | RES SMD 4.99K OHM 1% 1/16W 0402   |
| U1      | 1   | Microchip    | MIC2290YML-TR    | IC REG BOOST ADJ 750MA 8MLF       |

It is also availible though [*octopart*](https://octopart.com/bom-tool/Fi5WwdJ5)

## Assembly
Assembly is all surface mount with componets on one side of the board to make PNP assembly easy.

![assembly]

## Ordering
I havent tested the exported gerbers fully, I just upload the KiCad file. 

0.48 x 0.75 inches (12.1 x 19.1mm)

At OSH Park 3 boards will cost 1.75 USD

![renderTop]

[renderTop]:  /img/renderTop.png   "Render with view from above"
[renderIso1]: /img/renderIso1.png  "Isoemtric render from connector"
[renderIso2]: /img/renderIso2.png  "Isometric render from outputs"
[assembly]:   /img/assembly.png    "Assembly drawing for component positon"
[schematic]:  /img/schematic.png   "Schematic of the circuit"
