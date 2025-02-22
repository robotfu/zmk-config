## preprocessor macros

```devicetree
#include <dt-bindings/zmk/mouse.h>
#include <input/processors.dtsi>
#include <behaviors.dtsi>
#include <dt-bindings/zmk/bt.h>
#include <dt-bindings/zmk/keys.h>
#include <dt-bindings/zmk/pointing.h>
#include <dt-bindings/zmk/rgb.h>

#include "zmk-helpers/helper.h"
#include "zmk-helpers/key-labels/36.h"
/*

   &mmv_input_listener {
       input-processors = <&zip_xy_scaler 2 1>;
   };

   &msc_input_listener {
       input-processors = <&zip_xy_scaler 2 1>;
   };

 */

#define ZMK_MOUSE_DEFAULT_MOVE_VAL 1200  // 600
#define ZMK_MOUSE_DEFAULT_SCRL_VAL 20    // 10

#define KEYS_L LT0 LT1 LT2 LT3 LT4 LM0 LM1 LM2 LM3 LM4 LB0 LB1 LB2 LB3 LB4  // left hand
#define KEYS_R RT0 RT1 RT2 RT3 RT4 RM0 RM1 RM2 RM3 RM4 RB0 RB1 RB2 RB3 RB4  // right hand
#define THUMBS LH1 LH0 RH0 RH1                                              // thumbs
ZMK_HOLD_TAP(hml,
    flavor = "balanced";
    tapping-term-ms = <280>;
    quick-tap-ms = <175>;
    require-prior-idle-ms = <125>;
    bindings = <&kp>, <&kp>;
    hold-trigger-key-positions = <KEYS_R THUMBS>;
    hold-trigger-on-release;
)
ZMK_HOLD_TAP(hmr,
    flavor = "balanced";
    tapping-term-ms = <280>;
    quick-tap-ms = <175>;
    require-prior-idle-ms = <125>;
    bindings = <&kp>, <&kp>;
    hold-trigger-key-positions = <KEYS_L THUMBS>;
    hold-trigger-on-release;
)

```

## Nomod layer

```devicetree
        n0 {
            bindings = <
&kp ESCAPE  &kp Q  &kp W  &kp E  &kp R      &kp T                     &kp UP               &kp Y  &kp U      &kp I      &kp O    &kp P     &kp EQUAL
&kp TAB     &kp A  &kp S  &kp D  &kp F      &kp G           &kp LEFT  &none     &kp RIGHT  &kp H  &kp J      &kp K      &kp L    &kp SQT   &kp MINUS
&kp GRAVE   &kp Z  &kp X  &kp C  &kp V      &kp B  &to 0              &kp DOWN             &kp N  &kp M      &kp COMMA  &kp DOT  &kp FSLH  &kp BSLH
                          &mo 4  &kp SPACE  &mo 2                                          &mo 3  &kp LSHFT  &mo 5
            >;

            sensor-bindings = <&inc_dec_kp RIGHT_ARROW LEFT_ARROW>;
            label = "nomod";
        };

        n.lr {
            bindings = <
&none  &kp TAB   &none     &kp LC(LEFT_ARROW)  &kp LC(RIGHT_ARROW)  &kp C_VOLUME_UP                    &none         &kp PRINTSCREEN  &kp PG_UP  &kp UP         &kp PG_DN  &kp DEL   &none
&none  &kp LGUI  &kp LALT  &kp LCTRL           &kp LSHFT            &kp C_VOLUME_DOWN           &none  &none  &none  &kp CAPS         &kp LEFT   &kp DOWN       &kp RIGHT  &kp BSPC  &none
&none  &none     &none     &none               &none                &kp C_PLAY_PAUSE   &none           &none         &none            &kp HOME   &kp LG(SPACE)  &kp END    &kp RET   &none
                           &none               &none                &none                                            &none            &none      &none
            >;

            label = "nav_media";
        };

        n.rl {
            bindings = <
&none  &none  &kp N7  &kp N8  &kp N9  &none                  &none         &none  &none      &none      &none     &none     &none
&none  &none  &kp N4  &kp N5  &kp N6  &none           &none  &none  &none  &none  &kp LSHFT  &kp LCTRL  &kp LALT  &kp LGUI  &none
&none  &none  &kp N1  &kp N2  &kp N3  &none  &none           &none         &none  &none      &none      &none     &none     &none
                      &none   &kp N0  &none                                &none  &none      &none
            >;

            label = "number";
        };

        n.ll {
            bindings = <
&none  &none     &none     &none      &none      &none                  &none         &none  &kp LEFT_BRACE        &kp RIGHT_BRACE        &none          &none      &none
&none  &kp LGUI  &kp LALT  &kp LCTRL  &kp LSHFT  &none           &none  &none  &none  &none  &kp LEFT_PARENTHESIS  &kp RIGHT_PARENTHESIS  &kp SEMICOLON  &kp COLON  &none
&none  &none     &none     &none      &none      &none  &none           &none         &none  &kp LEFT_BRACKET      &kp RIGHT_BRACKET      &none          &none      &none
                           &none      &none      &none                                &none  &none                 &none
            >;

            label = "para";
        };

        n.rr {
            bindings = <
&rgb_ug RGB_BRI  &rgb_ug RGB_SPI  &rgb_ug RGB_SAI  &rgb_ug RGB_SPI  &rgb_ug RGB_EFF  &rgb_ug RGB_TOG                  &none         &none  &none      &none      &none     &none     &none
&none            &none            &none            &none            &none            &none                     &none  &none  &none  &none  &kp LSHFT  &kp LCTRL  &kp LALT  &kp LGUI  &none
&none            &bt BT_SEL 3     &bt BT_SEL 2     &bt BT_SEL 1     &bt BT_SEL 0     &bt BT_SEL 4     &none           &none         &none  &none      &none      &none     &none     &none
                                                   &none            &none            &none                                          &none  &none      &none
            >;

            label = "bt-rgb";
        };

        n.superi {
            bindings = <
&none  &none     &none     &none      &none      &none                    &none         &none    &none      &none      &none     &none     &none
&none  &kp LGUI  &kp LALT  &kp LCTRL  &kp LSHFT  &kp F11           &none  &none  &none  &kp F12  &kp LSHFT  &kp LCTRL  &kp LALT  &kp LGUI  &none
&none  &kp F1    &kp F2    &kp F3     &kp F4     &kp F5   &none           &none         &kp F6   &kp F7     &kp F8     &kp F9    &kp F10   &none
                           &none      &none      &none                                  &none    &none      &none
            >;
        };
```