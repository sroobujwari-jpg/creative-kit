// Natural Beauty Lens — By Esraa

// ====== Face Retouch Settings ======
var smoothSkin = 0.25;    // 0.0 – 1.0 (خفيف)
var brightness = 0.05;    // زيادة بسيطة
var contrast = 0.05;

// ====== Subtle Makeup ======
var lipTint = 0.15;       // شفاه وردي خفيف
var cheekGlow = 0.12;     // خدود طبيعية
var eyeGlow = 0.08;       // لمعة عيون بسيطة

// ====== Face Modifier ======
var noseScale = -0.08;    // تصغير خفيف للأنف
var mouthScale = 0.10;    // تكبير خفيف للفم
var faceScale = -0.03;    // تنحيف خفيف للوجه

// ====== References ======
var faceStretch = script.getSceneObject().getComponent("FaceStretch");
if (!faceStretch) {
    print("⚠️ Error: Add this script to a Face Stretch object.");
    return;
}

// ====== Apply Face Modifier ======
var noseRegion = faceStretch.createRegion();
noseRegion.center = new vec2(0.0, 0.2);
noseRegion.radius = 0.18;
noseRegion.strength = noseScale;

var mouthRegion = faceStretch.createRegion();
mouthRegion.center = new vec2(0.0, -0.18);
mouthRegion.radius = 0.22;
mouthRegion.strength = mouthScale;

var faceRegion = faceStretch.createRegion();
faceRegion.center = new vec2(0.0, 0.0);
faceRegion.radius = 0.35;
faceRegion.strength = faceScale;

// ====== Apply Retouch + Makeup ======
var faceRetouch = script.getSceneObject().getComponent("FaceRetouch");
if (faceRetouch) {
    faceRetouch.smoothness = smoothSkin;
    faceRetouch.brightness = brightness;
    faceRetouch.contrast = contrast;
    faceRetouch.lipTint = lipTint;
    faceRetouch.cheekGlow = cheekGlow;
    faceRetouch.eyeGlow = eyeGlow;
}

print("✨ Natural Beauty Lens Applied! Enjoy!");
