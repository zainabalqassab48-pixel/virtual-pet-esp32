# 🐾 ESP32 Handheld Virtual Pet

A handheld virtual pet built on an **ESP32** with a full-color **1.8" ST7735 TFT display**, three navigation buttons and a passive buzzer. Feed it, play with it, and keep its stats up.

Built by **Zainab Alqassab**, Computer Engineering student at **King Fahd University of Petroleum and Minerals (KFUPM)**.

<!-- Add a photo or GIF of your project here -->
<!-- ![Virtual Pet](images/demo.jpg) -->

---

## ✨ Features

- 🐶 **Animated pet** that walks left and right across the screen
- 📊 **Status screen** with Hunger, Fun and Happiness bars that drop over time
- 🍣 **Food menu** with Sushi and Chocolate, each affecting stats differently, plus an eating animation
- 🎾 **Play mode** with a bouncing animation that boosts fun and happiness
- 🎵 **Sound effects** and a startup jingle
- 🕹️ **Three-button navigation:** Scroll, Select and Back

---

## 🧰 Components

| Component | Quantity |
|---|---|
| ESP32 development board + ESP32 adapter board | 1 |
| 1.8" ST7735 TFT color display (128×160) | 1 |
| Push buttons | 3 |
| Passive buzzer | 1 |
| Breadboard | 1 |
| Jumper wires | As needed |

---

## 🔌 Wiring

### ST7735 display

| Display pin | ESP32 pin |
|---|---|
| VCC | 3.3V |
| GND | GND |
| SDA (DIN) | GPIO 22 |
| SCK (CLK) | GPIO 23 |
| CS | GPIO 19 |
| DC | GPIO 18 |
| RES (RST) | GPIO 21 |
| BL | GPIO 5 |

### Buttons and buzzer

| Component | ESP32 pin | Other leg |
|---|---|---|
| Scroll button | GPIO 13 | GND |
| Select button | GPIO 14 | GND |
| Back button | GPIO 16 | GND |
| Passive buzzer (+) | GPIO 15 | GND (−) |

All grounds connect to the breadboard's ground rail. The buttons use the ESP32's internal pull-up resistors (`INPUT_PULLUP`), so no external resistors are needed.

<!-- ![Wiring diagram](images/wiring.png) -->

---

## 💻 Software setup

1. Install the [Arduino IDE](https://www.arduino.cc/en/software).
2. Add ESP32 support: **Boards Manager** → search `esp32` → install **esp32 by Espressif Systems**.
3. Install these libraries from **Library Manager**:
   - `Adafruit GFX Library`
   - `Adafruit ST7735 and ST7789 Library`
4. Open `PROJ221.ino` (keep all `.h` files in the same folder).
5. Select **Tools → Board → ESP32 Dev Module** and the correct port.
6. Click **Upload**.

---

## 🎮 Controls

| Screen | Scroll | Select | Back |
|---|---|---|---|
| Title | Start | Start | Start |
| Pet | Open menu | — | — |
| Menu | Next option | Open option | Back to pet |
| Status | — | — | Back to menu |
| Food | Next food | Feed pet | Back to menu |
| Play | — | Play with pet | Back to menu |

---

## 📁 Project structure

```
game/
├── Game.ino    # Main program
├── pet.h          # Pet sprite (40×40, RGB565)
├── suchi.h        # Sushi sprite
├── chocolate.h    # Chocolate sprite
└── game.h         # Toy sprite
```

Sprites were converted from PNG images using [image2cpp](https://javl.github.io/image2cpp/) (40×40 canvas, white background, horizontal 2 bytes per pixel / RGB565).

---

## 🧠 What I learned

- Mapping board labels to GPIO numbers and adapting wiring to my ESP32 board
- Building a screen-based state machine with `enum` and `switch`
- Drawing sprites pixel by pixel with transparency from PROGMEM
- Debugging compiler errors and hardware issues (for example, GPIO 2 conflicting with the onboard LED)

---

## 🙏 Credits

This project is based on the excellent tutorial **"How To Build Your Own Virtual Pet | Arduino Engineering Tutorial"** by **Coco** ([Cocoas Aesthetic on YouTube](https://www.youtube.com/@CocoasAesthetic)), customized with my own sprites, foods and wiring.
