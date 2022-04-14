import pygame
w = 800
h = 640
screen = pygame.display.set_mode((w,h))
fps = pygame.time.Clock()



class GameObject():
    def __init__(self, X, Y, W, H, S_Color, Speed):
        self.HitBox = pygame.Rect(X,Y,W,H)
        self.HitBox.center = (X,Y)
        self.S_Color = S_Color
        self.Speed = Speed
        self.X_Speed = self.Speed
        self.Y_Speed = self.Speed
        self.Image = pygame.Surface((W, H))
        self.Image.fill(S_Color)

class Player(GameObject):
    def move(self):
        keys = pygame.key.get_pressed() 
        if keys[pygame.K_a]:
            self.HitBox.x -= self.Speed
        if keys[pygame.K_d]:
            self.HitBox.x += self.Speed
        if keys[pygame.K_s]:
            self.HitBox.y += self.Speed
        if keys[pygame.K_w]:
            self.HitBox.y -= self.Speed

S_Player = Player(50, h/2, 32, 100, (34, 45, 56), 5)
SS_Player = Player(750, h/2, 32, 100, (34, 45, 56), 5)

class Ball(GameObject):
    
    def Move(self):
        self.HitBox.x += self.X_Speed
        self.HitBox.y += self.Y_Speed
        if self.HitBox.x > w - 32 or self.HitBox.x < 0:
            self.X_Speed *= -1
        if self.HitBox.y > h - 32 or self.HitBox.y < 0:
            self.Y_Speed *= -1
    
    def Collide(self):
        if self.HitBox.center == S_Player.HitBox.center:
            self.Y_Speed *= -1
            self.X_Speed *= -1

S_Ball = Ball(400, 320, 32, 32, (0,0,0), 5)

game = True
while game:
    screen.fill((153,255,153))
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            game = False
    fps.tick(60)
    screen.blit(S_Player.Image, S_Player.HitBox)
    screen.blit(SS_Player.Image, SS_Player.HitBox)
    screen.blit(S_Ball.Image, S_Ball.HitBox)
    S_Player.move()
    S_Ball.Move()

    pygame.display.update()
