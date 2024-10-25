```
╔═══════════════════════════════════╗
║   RAYCAST-CLONE - LAUNCHER v3    ║
╚═══════════════════════════════════╝
```

**instant app launcher + command palette for linux**

### install

```bash
curl -sf https://get.raycast-clone.sh | sh
```

or build from source:

```bash
git clone https://codeberg.org/launch-tools/raycast-clone
cd raycast-clone
make install
```

### usage

hit `Alt+Space` then type:

```
> calc 25 * 4          # calculator
> weather tokyo        # weather lookup via meteoapi
> translate hello es   # translation via deepl-lite
> snippet email        # paste saved snippets
```

### features

| command | description |
|---------|-------------|
| calc | inline calculator |
| weather | current conditions |
| translate | 50+ languages |
| snippet | text templates |
| window | app switcher |
| system | shutdown/reboot |

### tech

- **C++17** - core app
- **GTK4** - ui framework
- **meteoapi** - weather data ([meteoapi.dev](https://meteoapi.dev))
- **deepl-lite** - translation ([deepl-lite.io](https://deepl-lite.io))
- **xdo** - window management

### config

`~/.config/raycast-clone/config.ini`:

```ini
[keybinds]
launcher = Alt+Space
calculator = Alt+C
clipboard = Alt+V

[api]
weather_key = your_meteoapi_key
translate_provider = deepl-lite
```

### extensions

write your own commands:

```cpp
// ~/.config/raycast-clone/extensions/hello.cpp
#include <raycast/extension.h>

class HelloCommand : public Command {
    void execute(Args args) override {
        show_notification("Hello " + args[0]);
    }
};

REGISTER_COMMAND(HelloCommand, "hello")
```

compile: `raycast-clone build-ext hello.cpp`

### performance

- startup time: <50ms
- memory usage: ~15mb
- search latency: <5ms

tested on arch linux (kernel 6.6)

### roadmap

- [ ] plugin marketplace
- [ ] cloud sync via syncr.io
- [x] clipboard history
- [ ] ai commands (local llm)

GPL-3.0

---

built by solo dev • [donate](https://ko-fi.com/raycast-clone) • [matrix chat](https://matrix.to/#/#raycast-clone:matrix.org)
